# Registros de pruebas y límites

Estos registros contienen ejemplos sintéticos, no un estudio con lectores ni una medición de fiabilidad general. Las respuestas de referencia no se incluyeron en las peticiones de generación. No se ejecutaron los comandos de los pasajes.

## Comparación con modelo identificado

La [comparación exploratoria](2026-10-17-version-comparison.md) enfrenta v0.1.1 con las instrucciones de `b7de0eb` mediante entradas comunes. Su [JSON completo](2026-10-17-version-comparison.json) conserva las dos ramas, los contextos, la configuración, las comprobaciones, las revisiones ciegas y sus desacuerdos. Incluye también una tanda excluida por avisos de la herramienta de lectura que contaminaron las referencias. Declara los ensayos anteriores que no se pudieron conservar.

El modelo resuelto fue `claude-sonnet-5-5`, mediante Claude Code 2.1.302 y esfuerzo `medium`. Las respuestas se generaron en procesos nuevos, sin herramientas, MCP, persistencia de sesión ni personalizaciones. Los ajustes no expuestos se registran como no disponibles. La prueba cargó las referencias manualmente: no demuestra activación automática ni carga selectiva.

Los juicios son de un modelo, no de lectores humanos. La rúbrica del revisor se corrigió tras el primer dictamen. Los casos estaban disponibles durante el desarrollo y no existe una reserva no vista. No se atribuye una mejora causal o general a esta ejecución.

## Línea base de traducción anterior

El [registro de doce traducciones](2026-10-17-translation-baseline.json) usa la guía v0.1.1 de `feef2aa2152e71f073254a1fba8947ae86b7d806` y el mismo modelo identificado. Conserva las respuestas crudas, las instrucciones completas y las opciones no disponibles. Los literales protegidos se conservaron en esa ejecución; no incluye aprobación semántica ni comprensión humana.

El identificador `unlimited-company` se hizo explícito en el corpus después de esa línea base. El registro conserva la entrada original, que podía leerse como una descripción traducible del plan. No compares su respuesta con una entrada posterior distinta. La comparación nueva conserva su propio corpus común.

## Registros históricos con alias de modelo

| Registro | Revisión de la guía | Solicitudes del corpus | Otras solicitudes | Rechazadas en aquella revisión |
| --- | --- | ---: | ---: | ---: |
| [0.1.0](2026-10-17-v0.1.0.json) | `d9d2a2f` | 19 | 2 | 0 |
| [0.1.1](2026-10-17-v0.1.1.json) | `e1bac76` | 21 | 2 | 0 |
| [Seguimiento de instrucciones genéricas](2026-10-17-generic-prompts.json) | `e1bac76` | 3 | 0 | 0 |

Estos archivos permanecen sin cambios. Las versiones usaron conjuntos distintos; los recuentos no miden mejora. Las otras solicitudes probaron el formato de revisión y la redacción de UI nueva. El seguimiento quitó recordatorios de conservación de tres tareas, sin regenerar las otras dieciocho respuestas ni cambiar la guía.

Cada JSON guarda las peticiones y respuestas, las huellas de los archivos de guía, una revisión fijada y la construcción del mensaje de sistema. La revisión indicada reconstruye las instrucciones; `case_revision`, o `guidance_revision` si no hay otra, fija los requisitos. Hubo una petición sin historial por entrada y no se proporcionaron herramientas.

Esos tres registros usaron el alias `default`. La interfaz no expuso proveedor resuelto, identificador de modelo, temperatura, límite de salida, semilla ni opciones de razonamiento. No permiten repetir exactamente el modelo ni compararlo con otro identificado. El revisor fue el asistente implementador. La revisión independiente de las instrucciones no validó comprensión ni seguridad de las salidas.

## Uso de estos resultados

Comprensión humana no evaluada. Las comprobaciones de cadenas no garantizan que cada literal conserve su condición y su acción. Una revisión por modelo puede equivocarse. Los textos con consecuencias legales, operativas o de seguridad requieren revisión de una persona que conozca el dominio. Ninguna ejecución garantiza el resultado de otra petición, modelo o contexto.
