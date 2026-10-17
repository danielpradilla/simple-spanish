# Activación y carga de referencias

## Objetivo y casos

Esta prueba comprueba si un agente descubre la skill, la selecciona cuando corresponde y lee las referencias indicadas. No mide por sí sola la fidelidad del resultado. Escribir en español no demuestra haber activado la skill.

[activation-cases.json](activation-cases.json) contiene tres peticiones técnicas positivas y dos negativas. Ninguna nombra la skill ni ordena usarla. Su contrato es distinto del de los corpus de reescritura:

- `id`: identificador estable.
- `request`: petición completa que recibe el agente.
- `expected_activation`: si debe seleccionar esta skill.
- `required_references`: lecturas necesarias para esta petición.
- `avoid_references`: archivos o prefijos cuya carga no se necesita en esta petición. No son prohibiciones generales para otros trabajos.

No cambies las peticiones ni las referencias esperadas después de ver una salida para convertir un fallo en aprobado. Los casos negativos no evalúan la calidad de la redacción inglesa ni del poema: solo la selección de esta skill y la ausencia de cargas ajenas a su alcance.

## Preparar un cliente nativo

1. Expón la skill mediante el mecanismo de descubrimiento del cliente, sin copiar sus instrucciones al mensaje del usuario ni al sistema de la prueba.
2. Conserva los contenidos y huellas de `SKILL.md` y sus referencias. Registra cliente, modelo resuelto, ajustes, herramientas, memoria y contexto que no puedas desactivar.
3. Comprueba que el cliente registra la skill. Si no aparece en su índice, la preparación ha fallado. No atribuyas su ausencia posterior a una mala descripción ni cuentes un caso negativo como aprobado.
4. Ejecuta cada petición exacta en un proceso o sesión nuevos. Conserva la traza, respuesta, errores y denegaciones. No permitas ejecutar los comandos del texto fuente.
5. Busca invocaciones de la skill y lecturas satisfactorias, con sus resultados. Un enlace, una mención o una solicitud de lectura fallida no demuestran que se cargara el archivo. Si el cliente inserta recursos automáticamente, conserva su contenido real; no infieras la carga a partir de un nombre.

No uses un modo que desactive las skills para medir su activación. La prueba de calidad con todas las referencias cargadas manualmente es otra prueba y debe quedar separada.

## Configuración ejercitada en Claude Code

El [registro completo](results/2026-10-17-native-activation.json) conserva las preparaciones, las dos variantes de instrucciones y todas las respuestas. Se usó Claude Code 2.1.302, modelo resuelto `claude-sonnet-5-5` y esfuerzo `medium`.

En dos controles iniciales, la ubicación de proyecto no apareció en el índice del entorno restringido, con ámbitos de configuración vacío y `project`. No se atribuye una causa no comprobada a esa ausencia. Para disponer de descubrimiento observable sin habilitar ajustes del usuario, se cargó explícitamente un plugin temporal que contenía solo los archivos documentales de la skill:

```text
<directorio-de-trabajo>/native-plugin/
├── .claude-plugin/plugin.json
└── skills/simple-spanish/
    ├── SKILL.md
    ├── LICENSE
    └── references/
```

Su manifiesto fue:

```json
{"name":"simple-spanish-evaluation","version":"0.2.0","description":"Temporary read-only fixture for skill discovery."}
```

No se añade ese plugin al paquete distribuido. Es una instalación temporal de prueba para este cliente, que registra el nombre `simple-spanish-evaluation:simple-spanish`.

Desde el directorio de trabajo, se envió cada `request` por la entrada estándar de un proceso nuevo con estas opciones:

```sh
claude --restricted --setting-sources "" \
  --plugin-dir /ruta/al/directorio-de-trabajo/native-plugin \
  --tools Read,Skill --allowedTools Read,Skill \
  --strict-mcp-config --mcp-config '{"mcpServers":{}}' \
  --permission-mode dontAsk --no-session-persistence \
  --output-format stream-json --verbose \
  --model claude-sonnet-5-5 --effort medium --max-budget-usd 1.00 -p
```

No se usó `safe-mode`, porque desactiva las skills. No se habilitó `bypassPermissions`. Solo se expusieron `Read` y `Skill`; el ejemplo de shell del README no se ejecutó. El sistema predeterminado y los plugins integrados del cliente permanecieron activos. No se presenta el entorno como una máquina limpia ni se afirma haber reconstruido todo el contexto del proveedor.

## Resultado con instrucciones finales y fixture incompleto

El cliente registró la skill en todos los casos. Este fixture contenía las referencias, pero no `evals/`; por tanto, no puso a prueba su exclusión. La tabla separa selección y lecturas. Los archivos se cuentan por llamadas `Read` satisfactorias observadas, no porque sus rutas aparezcan en la entrada principal.

| Caso | Selección esperada / observada | Referencias leídas | Lectura requerida no observada |
| --- | --- | --- | --- |
| Procedimiento en español | Sí / Sí | Ninguna | `use-cases.md` |
| Fragmento para traducir | Sí / Sí | `translation.md` | Ninguna |
| README para traducir | Sí / Sí | `translation.md`, `use-cases.md` | `documents.md` |
| Reescritura en inglés | No / No | Ninguna | Ninguna |
| Poema en español | No / No | Ninguna | Ninguna |

No se observaron lecturas de `sources.md`, que sí estaba disponible. La ausencia de lecturas de corpus, resultados o protocolo de lectores no es evidencia de exclusión: esos archivos no existían en el fixture. Sus comprobaciones figuran como no ejercitadas. Tampoco se garantiza un coste o una selección iguales en otra ejecución.

Las dos comprobaciones de referencias incompletas son fallos, aunque la selección de skill sea correcta. Además, el procedimiento final dejó la advertencia después de la acción afectada, en contra de SS-05. La activación no garantiza que se sigan las instrucciones.

La primera variante también omitió referencias. Entre ambas cambiaron `SKILL.md`, para combinar las lecturas cuando coinciden tipos de tarea, y `sources.md`, que añadió citas sobre formato y carga progresiva. No se observó lectura de `sources.md`. No se cambiaron peticiones ni criterios. El registro conserva ambas tandas y sus fallos; no se eligió una respuesta favorable entre repeticiones ni se convirtió el resultado posterior en evidencia de fiabilidad.

## Paquete completo disponible, sin inferencias del proveedor

Se preparó después un fixture con los 28 archivos existentes del paquete, incluidos corpus, resultados y protocolo de lectores. Se comprobaron los enlaces locales, incluido `references/documents.md` → `../evals/reader-study.md`. El [registro independiente](results/2026-10-17-native-full-package.json) conserva las huellas de todos los archivos suministrados, la misma guía y las cinco peticiones.

El proveedor rechazó las peticiones antes de generar respuestas: `is_error` es verdadero, `modelUsage` está vacío y los contadores de entrada y salida son cero. Aunque la CLI use el subtipo `success`, eso no es una respuesta válida a la tarea. Selección, lecturas y exclusión de materiales quedan como no evaluadas en esa tanda. No se cuentan las ausencias de llamadas como decisiones negativas ni como fallos semánticos.

## Reintento con el mismo paquete completo

El [reintento registrado](results/2026-10-17-native-full-package-retry.json) comenzó después de la disponibilidad anunciada por el proveedor. Hubo una solicitud nueva por caso, con las mismas peticiones, instrucciones, opciones y los mismos 28 archivos congelados. Las copias de README y de los informes son las de aquella preparación, no las del repositorio final. Sus huellas están conservadas. No se reemplazaron los rechazos ni las generaciones anteriores.

Las cinco peticiones recibieron respuestas del modelo `claude-sonnet-5-5` y el cliente registró la skill en todas:

| Caso | Selección esperada / observada | Referencias leídas | Lectura requerida no observada |
| --- | --- | --- | --- |
| Procedimiento en español | Sí / Sí | `use-cases.md` | Ninguna |
| Fragmento para traducir | Sí / Sí | `translation.md` | Ninguna |
| README para traducir | Sí / Sí | `translation.md` | `documents.md`, `use-cases.md` |
| Reescritura en inglés | No / No | Ninguna | Ninguna |
| Poema en español | No / No | Ninguna | Ninguna |

No se observaron lecturas de fuentes ni de los materiales de evaluación, que esta vez sí estaban disponibles. Esto ejercita su exclusión en estas cinco peticiones, no demuestra que se excluyan siempre. La carga de referencias del README volvió a fallar. El procedimiento situó la advertencia antes de la acción en esta salida; el fallo de la tanda anterior se conserva. Las diferencias entre salidas no se atribuyen causalmente al fixture ni permiten estimar fiabilidad.

## Formato, contexto y límites

Se comprueba que el nombre coincida con la carpeta, la descripción no supere 1024 caracteres, la versión esté declarada y la entrada principal permanezca por debajo de la recomendación de 500 líneas. No se añade una dependencia para validar estos campos. El cargador nativo también ejercita su interpretación real.

Las huellas y contenidos fijan las instrucciones exactas, aunque varias variantes de desarrollo declaren la misma versión antes del commit. No se infiere un recuento de tokens a partir de palabras o bytes. Las métricas de uso de la CLI incluyen el contexto del cliente y las llamadas sucesivas; no aíslan el coste de un archivo.

Esta ejecución no verifica todos los clientes ni la activación global en cada agente. No mide comprensión humana ni seguridad operativa. Antes de usar una salida en una operación con consecuencias, revisa sus hechos, condiciones, advertencias y literales. Los fallos nativos observados siguen siendo un límite de adopción.
