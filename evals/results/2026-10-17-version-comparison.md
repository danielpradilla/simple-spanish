# Comparación exploratoria de versiones

## Qué se ejecutó

Se compara la guía v0.1.1 (`feef2aa`) con las instrucciones de `b7de0eb`, no con una supuesta versión final posterior. Ambas reciben el corpus común de `b7de0eb`. Las entradas completas, instrucciones, configuración, respuestas crudas, comprobaciones y dictámenes están en el [registro JSON](2026-10-17-version-comparison.json).

Se incluyó una generación por caso y versión con `claude-sonnet-5-5`, Claude Code 2.1.302 y esfuerzo `medium`. Cada petición usó un proceso nuevo, sin herramientas, MCP, memoria de sesión ni personalizaciones. No se expusieron temperatura, semilla ni límite de tokens de salida. Las referencias y el sistema completos se cargaron manualmente: esta prueba no mide activación automática ni carga selectiva.

No hay casos reservados: todos estaban disponibles durante el desarrollo. Estos ejemplos sintéticos no miden una tasa de fallos de AssetGo.

## Conservación y revisión automática

La tabla reproduce el segundo dictamen del modelo, no una aprobación humana. Fiel, no fiel y dudoso son juicios globales sobre la salida; comprobar requisitos enumerados no basta si falta otro hecho del original.

Los recuentos de literales incluyen solo los casos cuya lista no está vacía. La columna muestra los casos sin pérdidas en base y candidata; no implica aprobación semántica.

| Corpus | Casos | Todos los literales: base / candidata | Fieles: base / candidata | No fieles: base / candidata | Dudosos: base / candidata |
| --- | ---: | ---: | ---: | ---: | ---: |
| Reescritura | 21 | 10 / 10 | 20 / 21 | 1 / 0 | 0 / 0 |
| Traducción | 12 | 8 / 8 | 11 / 12 | 0 / 0 | 1 / 0 |
| Documento completo | 2 | 2 / 2 | 2 / 2 | 0 / 0 | 0 / 0 |

En el documento con ejemplos, ambas ramas conservaron exactamente el bloque bash y la estructura Mermaid al sustituir solo sus etiquetas. Eso no prueba ejecución del código, navegación de enlaces ni renderizado del diagrama.

El caso `mensaje-existente-editable-con-literales` de la base cambió «pulse» por «pulsa» y añadió una nota fuera del mensaje solicitado. El revisor señaló el cambio de trato y el incumplimiento del formato. En `sintetico-commit-transaccion-bd`, la base omitió la indicación de ejemplo sintético; la segunda revisión lo marcó como dudoso en fidelidad e incompleto como traducción.

## Claridad percibida

Solo se comparó claridad cuando el segundo dictamen consideró fieles y conformes ambas salidas. Es preferencia de un modelo, no desempeño de lectores.

| Resultado del segundo revisor | Pares |
| --- | ---: |
| Preferencia por candidata | 6 |
| Preferencia por base | 5 |
| Equivalentes | 22 |
| No elegibles | 2 |

No se interpreta esta distribución como una mejora demostrada. Una generación por caso y una preferencia editorial no permiten atribuir el resultado a las instrucciones nuevas.

## Desacuerdos y límites de la revisión

El mismo modelo revisó a ciegas en contextos nuevos, sin conocer la correspondencia A/B. Se conservan la asignación, la rúbrica y las respuestas completas. No es independencia entre modelos ni revisión humana.

La primera revisión no desglosó cada requisito y marcó como fallo la instrucción «Haz una copia de seguridad… Verifica la copia…» por no repetir «obligatorio». El imperativo puede expresar obligación. Se corrigió esa instrucción del revisor y se realizó una segunda revisión con evidencia por requisito. El nuevo dictamen dejó de rechazar `obligacion-copia-verificada`, pero cambió `sintetico-commit-transaccion-bd` de fiel a dudoso. Ambos desacuerdos permanecen visibles, sin resolución de un especialista.

Las salidas del revisor tampoco siempre siguieron el formato JSON solicitado. El registro conserva las respuestas originales, las normalizaciones de nombres de campos y la evidencia del JSON adicional incluido en la misma respuesta. Una revisión omitió todos los requisitos; una petición complementaria los examinó sin reemplazar las traducciones originales. La revisión automática puede omitir criterios, inventar objeciones o confundir estilo con fidelidad.

La rúbrica del revisor se corrigió después de ver sus primeros dictámenes. Esta comparación es exploratoria, no un ensayo confirmatorio con todo el análisis fijado de antemano.

## Ensayos excluidos y evidencia ausente

Una tanda candidata recibió avisos de repetición de la herramienta de lectura dentro de cinco referencias. Se excluyó completa por contexto incorrecto, no por la calidad de sus salidas. El JSON conserva sus instrucciones y respuestas. La tanda incluida usa los contenidos exactos obtenidos de Git.

Un trabajo de revisión de esa tanda se interrumpió al perderse el entorno antes de conservar sus dictámenes; se desconoce cuántos terminaron. Tres respuestas de un ensayo anterior de desarrollo tampoco se guardaron por un fallo del primer comprobador. No se reconstruyen ni cuentan como aprobadas. Los borradores de casos se aclararon antes de fijar el corpus común; la línea base de traducción publicada antes mantiene su fuente original.

## Comprensión y alcance

Comprensión humana no evaluada. No se reclutó a participantes ni se simularon sus respuestas. No se afirma fiabilidad general, seguridad de producción ni conformidad con normas. Los textos que afectan a permisos, datos o riesgos requieren revisión del responsable del dominio.
