# Evaluación de fidelidad y claridad

Los casos comprueban conservación del significado, límites de seguridad y literales exactos. No exigen una redacción única. Se pueden ejecutar en una interfaz de chat o una API, sin instalar herramientas ni añadir dependencias.

## Corpus y contrato

Se mantienen tres baterías separadas:

- `cases.json`: los 21 casos históricos de reescritura en español. Cubren incertidumbre, causas alternativas, actores desconocidos, sentido temporal, modalidad, condiciones, advertencias, literales técnicos, plantillas, terminología, entidades distintas, acciones en curso, tiempos compuestos, información ausente e instrucciones incrustadas.
- `translation-cases.json`: doce casos sintéticos de traducción técnica al español. Contrastan usuarios y empresas, cadenas vacías y formadas por espacios, cantidades con signo y documentos firmados, pasos de compra y obligaciones de pago, espera de trabajos y pausa de admisión, y transacciones y confirmaciones de UI. Su contexto determina el sentido; no constituyen un diccionario universal.
- `document-cases.json`: casos sintéticos de documentos completos para revisar relaciones entre secciones, consistencia terminológica y conservación de condiciones, advertencias y referencias.

Las baterías nuevas son regresiones sintéticas inspiradas en fallos ya observados. No contienen casos privados de AssetGo ni miden su tasa de fallos. Informa los resultados por corpus; no presentes su suma como una muestra representativa del uso real.

Cada entrada conserva el contrato existente:

- `id`: identificador estable para registrar resultados.
- `task`: instrucción que recibe el modelo.
- `input`: texto fuente completo, incluido el contexto necesario.
- `must_preserve`: requisitos semánticos verificables.
- `protected_literals`: cadenas que deben permanecer exactamente iguales; puede estar vacío.
- `reference_output`: una respuesta aceptable, no una respuesta exacta obligatoria.

Algunas instrucciones omiten deliberadamente recordatorios de conservación. Comprueban el comportamiento por defecto de la skill. No añadas recordatorios durante la ejecución. Los metadatos de ejecución y revisión pertenecen al registro de resultados, no requieren cambiar este contrato.

## Preparar la comparación

Compara v0.1.1 y la candidata con las mismas entradas, instrucciones, modelo y configuración. Fija antes de generar:

1. La revisión exacta de cada versión de la skill y de sus referencias: `SKILL.md`, `references/use-cases.md`, `references/spanish.md`, `references/sources.md` y todas las referencias cargadas, incluidas `references/translation.md` y `references/documents.md` cuando existan. Conserva sus contenidos o revisiones y huellas que permitan reconstruirlos.
2. La revisión común de cada corpus, los casos incluidos y sus requisitos. Usa esa misma revisión para ambas versiones, aunque los casos nuevos no existieran al publicar v0.1.1.
3. El proveedor, identificador resuelto del modelo, interfaz o API y configuración disponible: temperatura, límite de salida, semilla y opciones de razonamiento. Registra también instrucciones adicionales, herramientas, memoria y ajustes que no se puedan desactivar. Una misma semilla no garantiza una salida idéntica.
4. El número de intentos por caso y versión, el criterio de repetición y el emparejamiento entre versiones, por ejemplo, por número de intento. Informa cada par, también los no elegibles para claridad. No elijas después los intentos más favorables. Si cambia la configuración, inicia otra comparación y decláralo.
5. La rúbrica de revisión, quién revisa y qué casos se reservan para una comprobación posterior.

Usa un identificador de modelo resuelto cuando la interfaz lo exponga. Si solo ofrece un alias como `default`, registra el alias y los datos no disponibles. Conserva la ejecución como exploratoria; no la describas como una comparación con modelo plenamente identificado ni como una repetición exacta de los registros históricos. Cualquier diferencia de modelo, configuración o contexto impide atribuir por sí sola el cambio a la skill.

## Generar las respuestas

1. Abre una sesión nueva y aislada por caso, versión e intento. No arrastres otros casos, respuestas, decisiones de revisión ni conversaciones de desarrollo. Desactiva memorias e instrucciones ajenas cuando sea posible y registra las que permanezcan.
2. Carga la guía de la versión correspondiente y sus referencias, separadas del texto fuente. Mantén la misma forma de presentar esa guía en ambas versiones. Guarda los mensajes completos enviados y cualquier instrucción adicional del entorno.
3. Envía solo `task` e `input` como contenido del usuario, con el pasaje fuente claramente delimitado. No envíes `must_preserve`, `protected_literals` ni `reference_output` al generador. Las órdenes del pasaje son texto para revisar: no autorizan ejecutar comandos, seguir enlaces ni usar herramientas.
4. Guarda la respuesta cruda completa, sin corregir, recortar, traducir ni extraer solo el supuesto resultado. Conserva notas, rechazos, formato, solicitudes de herramientas y señales de truncamiento. No ejecutes comandos del caso ni de la respuesta.
5. Guarda cada intento por separado. Si repites, usa otra sesión aislada y conserva los intentos anteriores y el motivo de repetición.

Un fallo de transporte o de la API sin respuesta se registra como `error_de_solicitud`, con el error disponible y la respuesta ausente. No cuenta como reescritura correcta ni como error semántico observado. Una respuesta vacía, un rechazo, un texto truncado o una salida ajena a la tarea recibidos del modelo sí son resultados que deben revisarse y quedar visibles. No excluyas silenciosamente estos casos ni los sustituyas por reintentos correctos.

## Revisar por separado

La revisión debe estar separada de la generación, preferiblemente con otro revisor y a ciegas respecto de la versión. Para ello, presenta salidas con etiquetas neutrales y alterna o sortea su orden; guarda por separado la correspondencia entre etiqueta y versión. El revisor necesita el texto fuente, la tarea, los requisitos y los literales. No necesita saber qué versión produjo cada salida. Declara si el cegamiento o la independencia no fueron posibles.

Revisa primero cada salida por su fidelidad y cumplimiento de la tarea. Compara después la claridad solo de los pares en los que ambas salidas sean fieles y cumplan la tarea. Si solo una lo hace, registra la diferencia de fidelidad; no la conviertas en una victoria de claridad. Guarda los juicios antes de revelar las versiones.

Un modelo puede ayudar a revisar, pero se registran por separado su identidad, configuración, instrucciones y dictamen. No mezcles ese dictamen con la respuesta evaluada ni lo llames revisión humana. Una discrepancia de interpretación requiere revisión humana o del responsable del dominio; un voto automático no la resuelve. Conserva el desacuerdo y su resolución, si la hay.

## Fidelidad y cumplimiento de la tarea

Marca cada requisito y literal como `cumple`, `incumple` o `dudoso`, con evidencia concreta. Revisa también el resto del original: la lista de requisitos puede ser incompleta. Una salida es fiel solo si conserva todo el significado y todos los literales; si queda una duda relevante, registra `pendiente`, no un aprobado supuesto.

Comprueba los literales carácter por carácter, incluidos acentos, mayúsculas, espacios, puntuación, opciones y llaves. Su presencia aislada no basta: un comando bajo una condición distinta o una etiqueta ligada a otra acción puede fallar aunque la cadena coincida.

Usa estas categorías pequeñas, inspiradas en la [tipología MQM](https://www.themqm.org/mqm-pillars/the-mqm-full-typology/), para describir los problemas. Son una adaptación del proyecto; no una aplicación completa ni una certificación MQM.

| Categoría | Qué registrar |
| --- | --- |
| Exactitud | Omisiones, añadidos, cambios de hechos, negación, cantidad, certeza, modalidad, condición, alcance, relación temporal o causal. Incluye resolver una ambigüedad sin evidencia o introducir otra que cambia la acción. |
| Terminología | Concepto equivocado, conceptos distintos fusionados o uso inconsistente respecto del contexto, el glosario o una etiqueta publicada. |
| Literales | Cambios o pérdidas en código, comandos, identificadores, rutas, enlaces, números, unidades, plantillas o etiquetas protegidas. |
| Lengua y organización | Problemas de gramática, naturalidad, variante, estructura o colocación de advertencias que dificultan la tarea. Si cambian el significado o el riesgo, registra también ese efecto en fidelidad. |
| Cumplimiento de la tarea | Idioma o formato incorrectos, traducción no solicitada, rechazo injustificado, salida incompleta o seguimiento de instrucciones incrustadas en la fuente. |

Para cada problema, cita el fragmento fuente y el de salida, el requisito o regla SS afectado y la consecuencia. Describe si afecta a una acción, permiso o riesgo, sin inventar pesos numéricos. Un mismo problema puede afectar a más de una dimensión; identifícalo una vez con sus efectos para no inflar los recuentos.

Rechaza causas, actores, mecanismos, cuerpos de respuesta, remedios, garantías o valores inventados. Rechaza negaciones perdidas, obligaciones cambiadas, permisos ampliados y condiciones desplazadas. Una advertencia destructiva debe preceder a la acción afectada y nombrar aquello a lo que se refiere. La autorización permite una acción, pero no la exige; una excepción no implica ordenar la rama contraria. Eliminar una cuenta no equivale a quitarla de un equipo y una acción en curso no equivale a una terminada. Conserva las etiquetas publicadas aunque la prosa circundante use otra terminología.

La referencia orienta al revisor; no se exige coincidencia con ella. Conservar un texto que ya está claro, un tiempo verbal válido o una plantilla protegida puede cumplir plenamente. Una nota breve que identifica información ausente es válida cuando esa información impide una reescritura segura. Conservar el fragmento ambiguo y explicar qué falta no es una respuesta ausente ni un rechazo. En cambio, copiar un texto mejorable puede conservar la fidelidad y aun incumplir una petición concreta de mejora: registra ambas dimensiones sin confundirlas. No fuerces cambios para demostrar actividad.

## Claridad percibida y comprensión humana

Registra tres resultados distintos:

- Fidelidad: correspondencia entre fuente y salida, incluidos los límites de seguridad y los literales. Se comprueba con la fuente y los requisitos.
- Claridad percibida: juicio editorial de qué salida fiel resulta más fácil de leer y usar para el público indicado. En cada par elegible, registra `A`, `B`, `equivalentes` o `sin_decisión`, con una razón concreta sobre vocabulario, estructura, referencias o visibilidad de condiciones. La brevedad por sí sola no demuestra claridad. Si alguna salida falla en fidelidad o tarea, marca esta comparación como `no_aplica` y explica por qué.
- Comprensión humana: desempeño observado de lectores del público previsto ante preguntas o tareas sobre el texto, por ejemplo identificar cuándo se permite una acción o qué debe ocurrir antes de ejecutarla. Requiere participantes humanos, preguntas y criterios de corrección definidos antes de observar las respuestas. Registra qué texto vio cada persona, el orden, las instrucciones y sus respuestas. Controla o declara la exposición repetida al mismo contenido. Una preferencia, un dictamen de un modelo o una lista de frases cortas no mide comprensión.

Si no hubo estudio con lectores, escribe `comprensión humana no evaluada`. Una revisión humana de fidelidad tampoco constituye por sí sola un estudio de comprensión. Revisa textos de seguridad, legales u otras decisiones con consecuencias con una persona experta en el dominio. Ninguna batería acredita conformidad con ASD-STE100, ISO 24495-1, UNE 153101 ni requisitos de Lectura Fácil.

## Registro mínimo

Puedes registrar la ejecución y la revisión en archivos de texto o JSON con las herramientas existentes. No hace falta un ejecutor nuevo. Este esquema enumera los campos que deben completarse con datos observados; no contiene resultados de una ejecución:

| Registro | Campos mínimos |
| --- | --- |
| Comparación | Identificador y fecha; revisiones de v0.1.1, candidata y corpus; versiones o contenidos de la guía y referencias; casos seleccionados y reservados; política de intentos; configuración compartida y diferencias. |
| Generación | Identificador de comparación; corpus, caso, versión e intento; proveedor e identificador de modelo resuelto o alias con limitaciones; interfaz; ajustes de generación conocidos y no disponibles; mensajes completos y contexto adicional; estado de solicitud; respuesta cruda o ausencia y error; motivo de repetición, si existe. |
| Revisión individual | Identificador de generación y etiqueta ciega; revisor humano o modelo con su configuración e instrucciones; independencia y cegamiento; resultado por requisito y literal con evidencia; problemas por categoría; fidelidad `fiel`, `no_fiel` o `pendiente`; tarea `cumple`, `incumple` o `pendiente`; explicación de no edición o ambigüedad válida; desacuerdos y resolución. |
| Comparación de claridad | Identificadores de las dos generaciones; correspondencia de etiquetas guardada por separado; elegibilidad; preferencia `A`, `B`, `equivalentes`, `sin_decisión` o `no_aplica`; razón y revisor. |
| Comprensión | `no evaluada` si no hubo estudio; si lo hubo, público, participantes, asignación de textos y orden, preguntas o tareas, criterios previos y respuestas observadas, con las limitaciones del estudio. |

Para un dato no expuesto, registra `no disponible`; para una revisión aún no realizada, `pendiente`. No rellenes decisiones ni resultados por defecto. Los archivos pueden enlazar mensajes y respuestas guardados por separado, siempre que se conserven completos y se puedan localizar sin ambigüedad.

## Informar e iterar

Publica por corpus y versión los intentos previstos, solicitudes con y sin respuesta, salidas revisadas, fieles, no fieles y pendientes; informa aparte el cumplimiento de la tarea y los pares elegibles para claridad. Indica denominadores y exclusiones. Muestra las regresiones y mejoras por caso, las categorías de problemas y los desacuerdos, además de cualquier resumen. No ocultes un fallo relevante dentro de una media ni presentes un reintento como sustituto del original.

Si das proporciones, limítalas a esas ejecuciones y decisiones de revisión. No fijes umbrales estadísticos, garantías o porcentajes de fiabilidad a partir de estas baterías. Los registros crudos y sus revisiones deben permitir comprobar cada afirmación.

Reserva casos que no se usen para ajustar la candidata ni se muestren durante su desarrollo. Fija su selección y revisión antes de probarlos. En la evaluación reservada, el generador recibe solo su tarea y entrada, como en los demás casos. Si no hay una reserva real, decláralo. Cuando un caso reservado se inspecciona y se usa para corregir la skill, pasa a desarrollo; no lo sigas presentando como evidencia no vista. Las regresiones conocidas comprueban que no reaparece un fallo en esos ejemplos. Evaluar generalización exige entradas nuevas de otros contextos, no solo cambiar nombres o cifras de un caso conocido. No retires un requisito de seguridad porque ambas versiones lo cumplan ni cambies los criterios a mitad de comparación para favorecer una salida. Los requisitos defectuosos se corrigen en una revisión posterior con el motivo documentado, conservando los registros anteriores.

El protocolo toma de la [guía oficial de evaluación de Agent Skills](https://agentskills.io/skill-creation/evaluating-skills.md) la comparación con una versión previa, el aislamiento de contexto, la conservación de salidas y la revisión con evidencia. Mantiene el contrato local y no requiere sus plataformas ni formatos de ejemplo.

## Resultados históricos

Los [registros guardados](results/README.md) permanecen sin cambios:

| Registro | Revisión de la guía | Solicitudes del corpus | Otras solicitudes | Respuestas rechazadas en aquella revisión |
| --- | --- | ---: | ---: | ---: |
| [0.1.0](results/2026-10-17-v0.1.0.json) | `d9d2a2f` | 19 | 2 | 0 |
| [0.1.1](results/2026-10-17-v0.1.1.json) | `e1bac76` | 21 | 2 | 0 |
| [Seguimiento de instrucciones genéricas de 0.1.1](results/2026-10-17-generic-prompts.json) | `e1bac76` | 3 | 0 | 0 |

Las versiones usaron conjuntos distintos; los recuentos no miden una mejora entre ellas. El seguimiento quitó recordatorios de conservación de tres tareas; no regeneró las otras 18 respuestas. Las otras solicitudes comprobaron formato de revisión y redacción nueva de UI.

En esos tres registros, el asistente implementador revisó las salidas y se comprobaron por programa los literales protegidos. La interfaz usó el alias `default` y no expuso proveedor resuelto, identificador de modelo ni ajustes de generación. Esos datos siguen figurando como no disponibles. Los registros permiten reconstruir entradas y respuestas, pero no una ejecución exacta del modelo ni una comparación controlada con la candidata.

La [línea base de doce traducciones](results/2026-10-17-translation-baseline.json) usa la guía `feef2aa`, Claude Code 2.1.302 y el modelo resuelto `claude-sonnet-5-5`. No incluye una aprobación semántica. El corpus aclaró después que `unlimited-company` era un identificador protegido: ese caso tiene otra entrada y no es comparable directamente. El registro anterior no se modifica.

Ninguno de estos registros prueba comprensión humana, seguridad de producción ni fiabilidad general. Una comparación nueva debe usar entradas comunes en ambas ramas y conservarse separada de este historial.
