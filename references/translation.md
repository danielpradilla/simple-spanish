# Traducción técnica con contexto

Esta guía aplica SS-01, SS-02, SS-03 y SS-07. Traduce solo si el usuario lo pide. No impone equivalentes universales ni autoriza cambiar requisitos.

## Identifica el concepto antes de elegir la palabra

Lee las definiciones y las secciones relacionadas disponibles. Identifica qué entidad se modifica, qué propiedad se limita y qué efecto tiene la operación. Una expresión abreviada puede depender de una definición anterior.

Consulta el glosario del proyecto si existe. No exijas crear un archivo nuevo para traducir un fragmento. Para un documento grande basta una lista breve de conceptos con su equivalente aprobado, la definición que lo respalda y los conceptos que deben mantenerse distintos. Si el glosario contradice la fuente o una etiqueta publicada, señala el conflicto; no lo resuelvas inventando una regla del producto.

Por ejemplo, un plan puede permitir usuarios ilimitados por empresa y limitar la cantidad de empresas. Conserva ambas dimensiones. No deduzcas qué es ilimitado solo por el nombre del plan.

Si falta contexto y elegir un sentido cambia una acción, un permiso o un riesgo, conserva el término o fragmento y añade la nota breve prevista en SS-03. Nombra la definición que falta. No elijas la interpretación más habitual como si fuera un hecho.

## Contrasta sentidos, no hagas sustituciones globales

Los siguientes ejemplos son sintéticos y solo ilustran el contexto indicado:

| Expresión | Contexto que decide el sentido |
| --- | --- |
| `signed` | Una cantidad puede tener signo; un documento puede llevar firma. No son requisitos equivalentes. |
| `nonblank` | Conserva la definición de caracteres admitidos. No lo reduzcas a «no vacío» si una cadena de espacios se rechaza. No añadas reglas de `null`, recorte o Unicode que la fuente no describa. |
| `checkout` | Puede nombrar un paso de compra o el préstamo de un equipo. En un contrato, omitir el paso del proveedor no elimina por sí solo una obligación de pagar. |
| `drain` | Si la fuente exige dejar de admitir trabajos y esperar a los activos, conserva ambas acciones. Una pausa de admisión no demuestra que todos hayan terminado. No añadas ese protocolo cuando no esté definido. |
| `commit` | Puede referirse a una transacción o a Git. No lo confundas con una confirmación de UI. Conserva el término estable del proyecto si ayuda a distinguirlos. |

Una traducción puede conservar el término técnico y explicar su sentido cuando la fuente lo define. No añadas una explicación por conocer un producto parecido.

## Comprueba las decisiones que describe el texto

Compara las respuestas del original y de la traducción a estas preguntas.
Úsalas cuando correspondan al pasaje; no inventes una respuesta que falte.

- ¿Qué entidad tiene cada límite y cuál es su base: por usuario, empresa o periodo?
- ¿Qué valores se admiten y cuáles se rechazan, incluidos los casos frontera descritos?
- ¿La condición es necesaria, suficiente o ambas? «Solo si» no ordena la rama contraria.
- ¿La frase concede permiso, expresa capacidad u obliga a actuar?
- ¿Qué sigue ejecutándose y qué debe terminar antes de pasar al siguiente paso?
- ¿La confirmación procede de una persona o describe un resultado guardado?

Conserva el tipo de cantidad que la fuente define. No conviertas un valor
numérico en un importe monetario si no se indica que sea dinero. Tampoco
añadas unidades o garantías para que la frase parezca más concreta.

## Recursos relacionados

- [Gramática y terminología](spanish.md): modalidad, tiempos, variantes y términos distintos.
- [Fuentes](sources.md): procedencia y límites de las recomendaciones.
