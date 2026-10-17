# Gramática y terminología

Estas pautas aclaran decisiones de las reglas SS-06 a SS-11.
Son preferencias editoriales del proyecto. No son prohibiciones generales
de la gramática española.

## Actores y voz

Nombra al actor si la fuente lo identifica y ayuda a entender la acción.
No deduzcas que actuó una persona, un agente o el sistema por la forma pasiva.
El sujeto omitido es natural en español cuando su referencia está clara.

> Se eliminaron tres archivos. No se conoce el actor.

Puede mantenerse así. «El sistema eliminó tres archivos» añade un actor
que no aparece en la fuente. «Los archivos se perderán» tampoco permite
concluir que un sistema los eliminará.

## Duda, obligación y tiempo

«Debe», «se recomienda», «puede» y «podría» no son intercambiables.
«Puede» también puede expresar capacidad o permiso: usa el contexto, no una
tabla de sustituciones. Conserva el matiz si el contexto no lo resuelve.

No elimines el subjuntivo de «siempre que la copia se haya verificado».
Tampoco cambies «podría haber fallado» por «falló» ni «está procesando» por
«procesó». La primera versión expresa algo que la segunda no conserva.

## Gerundios

El gerundio puede expresar una acción en curso, simultaneidad, modo u otras
relaciones válidas. RAE/ASALE también admite ciertos usos de posterioridad
cuando hay sucesión inmediata o un vínculo lógico claro. No los marques
como incorrectos por su terminación.

> El servicio está procesando la cola.

No necesita cambios por contener un gerundio.
Si una construcción deja dudas sobre el actor o el orden, aclárala con la
información disponible. Si no se conoce la relación, señala la duda en vez
de inventar «después», «por eso» o un actor.

## Actual y otros posibles calcos

En español, «actual» puede significar presente. «La versión actual» es una
expresión válida. No la cambies por «esta versión» sin comprobar la referencia.
«Usuario actual» no demuestra por sí solo que se trate del usuario autenticado.

En una traducción, el inglés «actual» suele corresponder a «real» y «actually»
a «en realidad». «Current» puede corresponder a «actual». Decide por el
significado de la frase, no por el parecido de las palabras.

«Eventualmente» no equivale automáticamente al inglés «eventually».
Conserva su sentido de posibilidad u ocasionalidad cuando sea el de la fuente.
No sustituyas «a veces» por «al final».

## Términos distintos

Mantén un término estable por concepto, no una palabra única para toda acción parecida.

| Distinción | Qué se debe conservar |
| --- | --- |
| Usuario y cuenta | Pueden ser objetos distintos del dominio. |
| Quitar de un grupo y eliminar | La primera acción puede cambiar solo la pertenencia. |
| Detener y forzar la terminación | No prometen el mismo cierre ni la misma conservación de datos. |
| Verificar y validar | Una comprobación de estado no es siempre una validación de esquema. |
| Admitir una actualización y actualizar | La capacidad no demuestra que la acción haya ocurrido. |
| Reintentar y recuperar | Repetir una operación no garantiza recuperar datos. |

Consulta el glosario del proyecto antes de cambiar un término.
Conserva términos técnicos estables como `commit` o `webhook` si la audiencia
los usa. No cambies etiquetas publicadas para imponer una preferencia léxica.

## Variante regional y formato

«Archivo» y «fichero» pueden ser opciones válidas según el proyecto y el público.
No conviertas una preferencia regional en un error lingüístico.
Mantén `tú`, `usted`, `vos` o el tratamiento definido por el producto.

No cambies separadores decimales, formatos de fecha, zonas horarias ni unidades
durante una reescritura. Si la tarea exige localizarlos, comprueba primero la
región y la interpretación del valor. Una fecha ambigua requiere contexto.

## Límites de longitud

Los objetivos de 20 y 25 palabras ayudan a detectar oraciones difíciles.
No son una medida de comprensión ni una prueba de conformidad.
Si se cuentan palabras, usa unidades separadas por espacios, no tokens del modelo.
No cortes una condición, una excepción ni un literal para cumplir el objetivo.

Las fuentes concretas están en [sources.md](sources.md).
