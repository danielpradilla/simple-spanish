# Ejemplos de reescritura

Estos ejemplos muestran resultados aceptables, no salidas obligatorias.
La forma puede variar si se conserva el significado.

## Error con causas posibles

Original:

> Se ha producido un error durante el procesamiento de su solicitud debido a un posible problema con el formato de los datos o con la versión del cliente.

Revisión:

> La solicitud falló. La causa podría ser el formato de los datos o la versión del cliente.

Se conservan las dos causas como posibilidades. No se afirma que el cliente
esté desactualizado ni que un campo concreto sea incorrecto.

## Respuesta posible de una API

Original:

> Si se envían datos no válidos, el endpoint podría responder con un error `400`, indicando un problema con los datos.

Revisión:

> Si los datos enviados no son válidos, el endpoint podría responder con un error `400` que indica un problema con los datos.

No se convierte la posibilidad en una garantía. Tampoco se inventa la
estructura del cuerpo de respuesta.

## Capacidad y acción

Original:

> El sistema admite la actualización del perfil del usuario actual.

Revisión:

> El sistema permite actualizar el perfil del usuario actual.

No se afirma que el sistema actualice el perfil por sí solo.
«Actual» sigue siendo válido y no se sustituye por un usuario diferente.

## Riesgo antes de una instrucción

Original:

> Ejecuta `storage purge --project demo` solo si verificaste la copia de seguridad. El comando elimina todos los archivos del proyecto `demo` y no permite deshacer la eliminación.

Revisión:

> El comando elimina todos los archivos del proyecto `demo`. No se puede deshacer la eliminación.
> Solo si verificaste la copia de seguridad, ejecuta `storage purge --project demo`.

Se conserva el comando, el alcance, la irreversibilidad y la condición.
La advertencia aparece antes de la acción afectada.

## Actor desconocido

Original:

> Se ha procedido a la eliminación de tres archivos. No se conoce quién efectuó dicha eliminación.

Revisión:

> Se eliminaron tres archivos. No se sabe quién los eliminó.

No se añade un operador ni un sistema para forzar la voz activa.

## Recomendación y permiso

Original:

> Se recomienda que active las alertas. Si así lo desea, puede desactivar los avisos por correo.

Revisión:

> Se recomienda activar las alertas. Si lo desea, puede desactivar los avisos por correo.

La recomendación no se convierte en una obligación. La segunda acción sigue
siendo opcional y mantiene el trato de usted.

## UI publicada y conceptos distintos

Original:

> Para proceder a quitar a una persona del grupo, pulse `Quitar miembro`. Esta operación no elimina su cuenta.

Revisión:

> Para quitar a una persona del grupo, pulse `Quitar miembro`. Esta acción no elimina su cuenta.

La etiqueta publicada se conserva. Quitar una pertenencia no se convierte
en eliminar una cuenta.

## Texto que ya es claro

Original y resultado:

> La versión actual está procesando la cola. El trabajo podría haber fallado antes de guardar el resultado.

Se conservan «actual», el gerundio de acción en curso y la posibilidad de un
fallo anterior. La presencia de esas formas no exige una corrección.
