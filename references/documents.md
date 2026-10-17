# Documentos completos e integridad

Aplica SS-01 a SS-04 antes de cambiar estructura o formato. Una traducción de prosa no autoriza cambiar el comportamiento de una aplicación ni su interfaz publicada.

## Conserva el contexto entre secciones

Antes de dividir un documento, localiza las definiciones, el glosario, los requisitos y las excepciones que afectan a otras secciones. Da a cada fragmento el contexto que necesita, sin inventarlo. Una definición al principio sigue aplicándose a los pasos posteriores.

Después de revisar los fragmentos, lee el resultado completo. Comprueba que los términos conservan el concepto, los pronombres tienen antecedente y cada requisito sigue unido a la acción afectada. Los títulos deben permitir encontrar el contenido que anuncian. No conviertas el documento en un resumen salvo que se pida.

## Distingue prosa y contratos

- La prosa y los títulos son editables dentro del alcance solicitado.
- El código ejecutable conserva comentarios, cadenas, opciones, espacios y orden. No ejecutes ejemplos para traducirlos.
- En un diagrama documental cuya traducción esté autorizada, edita solo las etiquetas explicativas. Conserva identificadores, conexiones, dirección, formas y sintaxis. Una etiqueta que cita una UI publicada sigue siendo un literal protegido.
- Conserva claves, valores contractuales y evidencia histórica de datos estructurados. No traduzcas un JSON por su extensión ni lo excluyas siempre: distingue texto de presentación y datos que consume una herramienta, según la tarea.

Si no puedes distinguir la capa editable sin cambiar una acción o un contrato, conserva el fragmento y señala qué información falta.

## Comprueba enlaces y referencias

Conserva los destinos de enlaces, rutas y anclas publicadas. Si traduces un título del que depende un enlace, conserva el ancla anterior con el mecanismo que admita el formato. Comprueba que siga apuntando a la sección correcta; no basta con que la URL continúe presente.

Si hay citas por número de línea, conserva su correspondencia o actualiza las referencias dentro del alcance autorizado. No impongas números de línea fijos a todos los documentos. Mantener el total de líneas no demuestra que las citas apunten al mismo contenido.

Algunos encabezados o fragmentos también son entradas de herramientas. Identifica el literal que exige ese consumidor y consérvalo. No cambies el parser, regeneres aprobaciones ni renombres claves para facilitar una traducción editorial. Si el contrato no está disponible, señala ese límite.

## Revisión final del documento

Recorre una tarea usando las secciones finales, no solo los párrafos aislados. Verifica condiciones, negaciones, advertencias y referencias cruzadas. Comprueba los ejemplos y diagramas contra la fuente. No declares enlaces, ejecución o renderizado verificados si solo comparaste su texto.

Comprueba que el lector pueda encontrar la acción permitida, sus condiciones, el resultado y el riesgo que la fuente describe. Si falta uno de esos datos, señálalo; no lo inventes para completar la lista. Esa comprobación editorial no demuestra comprensión. El [piloto con lectores](../evals/reader-study.md) separa tareas, dudas y opinión de claridad.
