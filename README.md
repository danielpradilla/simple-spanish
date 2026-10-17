# Simple Spanish

Skill para redactar, traducir al español y revisar documentación técnica. Su prioridad es conservar el significado antes de mejorar el estilo.

Se inspira en [ESTE](https://github.com/esadrian/este-skill) y [Simple English](https://github.com/AminBlg/SimpleEnglish). Adapta sus patrones útiles y corrige hallazgos de una revisión de adopción. Es un proyecto independiente, no una versión oficial de esas skills.

<a id="install-and-use"></a>

## Instalación global

En un agente compatible con la CLI de skills:

```sh
npx skills add danielpradilla/simple-spanish -g
```

También puedes copiar este repositorio al directorio de skills de tu agente, dentro de `simple-spanish/`. Mantén `SKILL.md` y sus carpetas relativas juntas. El paquete no incluye dependencias de ejecución, scripts, hooks ni instalador propio. La CLI de skills es una herramienta externa.

## Uso

```text
Reescribe este procedimiento con simple-spanish.
Traduce esta documentación al español. Conserva los comandos y las etiquetas publicadas.
Revisa este mensaje de error sin añadir causas ni soluciones.
```

El agente debe poder descubrir la skill. Su descripción incluye disparadores de español claro y traducción técnica; también puedes nombrarla de forma explícita. La activación automática depende del cliente y del modelo.

La respuesta esperada en una reescritura es solo el texto revisado, salvo que falte información necesaria y deba señalarse una ambigüedad. En una revisión, se pide informar del problema, el fragmento original, el ID de regla y una corrección que conserve el significado. Las instrucciones piden respetar el formato solicitado, sin imponer español a toda la conversación ni cambiar la configuración del agente.

<a id="rules-that-protect-meaning"></a>

## Prioridades de revisión

- Conservar hechos, incertidumbre, negaciones, obligaciones, permisos, condiciones y excepciones.
- Conservar código, comandos, marcadores, rutas, errores citados y etiquetas publicadas. La prosa de un mensaje de UI es editable si esa es la tarea; sus literales citados siguen protegidos.
- Colocar la advertencia antes de la acción afectada y la condición antes del mandato.
- No inventar actores, causas, campos de respuesta, pasos de recuperación ni garantías.
- Distinguir usuario y cuenta, quitar una pertenencia y eliminar un registro, pausar y esperar a que terminen los trabajos.
- Usar español natural, con gerundios válidos, subjuntivo y tiempos compuestos cuando aporten significado.

Los objetivos de longitud son ayudas editoriales, no pruebas de conformidad. No se hacen sustituciones automáticas ni se impone un diccionario universal.

## Traducción y documentos completos

La [guía de traducción](references/translation.md) pide consultar definiciones, contexto y glosarios antes de elegir equivalentes. Contrasta conceptos como cantidad con signo y documento firmado, o confirmación de UI y transacción guardada.

La [guía documental](references/documents.md) indica cómo conservar las relaciones entre secciones, los enlaces, las anclas, los ejemplos y los diagramas. Traducir prosa no autoriza cambiar código, contratos de datos ni etiquetas de una interfaz publicada.

La entrada principal pide leer todas las referencias que correspondan y no cargar los corpus ni los resultados al redactar. La [prueba nativa](evals/activation.md) registró lecturas incompletas: son instrucciones, no un comportamiento garantizado.

<a id="example"></a>

## Ejemplo

Original:

> Se recomienda que active las alertas. Si así lo desea, puede desactivar los avisos por correo.

Revisión:

> Se recomienda activar las alertas. Si lo desea, puede desactivar los avisos por correo.

La recomendación sigue siendo una recomendación. Desactivar los avisos sigue siendo opcional. Hay [más ejemplos](examples/before-after.md) de incertidumbre, comandos destructivos, actores desconocidos y etiquetas existentes.

<a id="sources-and-design-choices"></a>

## Fuentes y decisiones

El [registro de fuentes](references/sources.md) fija las revisiones consultadas de ESTE y Simple English y explica qué se adapta y qué se cambia.

Las fuentes también incluyen a la Comisión Europea, Microsoft, RAE/ASALE, MQM y Agent Skills, además de estudios sobre evaluación con lectores. Se distinguen las guías de estilo, la revisión de fidelidad y la comprensión observada. Su inclusión no implica respaldo a este proyecto ni permite transferir automáticamente sus resultados a esta skill.

<a id="regression-cases"></a>

## Pruebas y evidencia

- [Reescritura](evals/cases.json), [traducción contrastiva](evals/translation-cases.json) y [documentos completos](evals/document-cases.json): pasajes, requisitos semánticos y literales protegidos. Las referencias son respuestas posibles, no cadenas obligatorias.
- [Protocolo de comparación](evals/README.md): entradas comunes, versiones fijadas, contextos independientes y revisión separada de fidelidad y claridad.
- [Activación y carga de referencias](evals/activation.md): peticiones positivas y negativas con lecturas observables en un cliente nativo.
- [Piloto con lectores](evals/reader-study.md): dos pasajes, diez tareas, claves y asignación que evita mostrar ambas versiones del mismo contenido a una persona. No hay participantes ni resultados humanos.
- [Registros y límites](evals/results/README.md): respuestas crudas, configuración, revisiones, desacuerdos y ensayos excluidos. La comparación histórica de `b7de0eb` no se presenta como una prueba de instrucciones posteriores.

La coincidencia de literales no demuestra fidelidad. La preferencia de un modelo no mide comprensión. Los [cambios publicados](CHANGELOG.md) mantienen estas distinciones.

<a id="scope-and-limits"></a>

## Límites

El alcance es la prosa técnica y factual, no la escritura creativa ni el marketing. Las instrucciones no garantizan que un modelo las siga ni que cada lector entienda el resultado. Una persona que conozca el dominio debe revisar los textos con consecuencias de seguridad, legales u operativas.

La prueba nativa observó referencias obligatorias omitidas y una advertencia situada después de la acción afectada. Esos fallos se conservan en los resultados. La activación correcta no basta para adoptar salidas sin revisión.

No se declara conformidad con ASD-STE100, ISO 24495-1, UNE 153101 ni requisitos de Lectura Fácil. El paquete no incluye un diccionario de normas. Una regla del inglés no es automáticamente válida en español.

<a id="license"></a>

## Licencia

[MIT](LICENSE). Se conservan los avisos de esadrian y AminBlg. Las guías externas mantienen sus condiciones de uso; no se distribuyen sus textos completos.
