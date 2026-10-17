# Fuentes y decisiones de diseño

Fuentes consultadas el 17 de octubre de 2026.
Las recomendaciones se adaptan con palabras propias. Cada fuente conserva
su autoría y sus condiciones de uso. Su inclusión no implica respaldo a este proyecto.

## Skills de origen

### ESTE, de esadrian

- [Repositorio y revisión consultada](https://github.com/esadrian/este-skill/tree/93c08f4c18ffd5afdd33b67a1a12920a90ac04fd).
- Versión declarada: 0.1.0.
- [Licencia MIT](https://github.com/esadrian/este-skill/blob/93c08f4c18ffd5afdd33b67a1a12920a90ac04fd/LICENSE), Copyright (c) 2026 esadrian.

ESTE inspira el alcance de español técnico, la consistencia por concepto,
los IDs de reglas y la atención a actores, gerundios y cambios de trato.
Simple Spanish es una adaptación independiente, no una versión oficial de ESTE.

La revisión de adopción detectó estos problemas en esa revisión concreta:

| Hallazgo | Decisión de Simple Spanish |
| --- | --- |
| Algunos ejemplos convierten causas posibles en hechos y añaden detalles de una respuesta de API. | SS-01 y SS-03 prevalecen sobre todas las preferencias de estilo. Los ejemplos conservan la incertidumbre. |
| La regla de «actual» invierte su relación con el inglés «current». | Se admite «actual» con el sentido de presente. |
| Algunos ejemplos de voz activa añaden un operador o un sistema no identificado. | Se mantiene la pasiva si se desconoce el actor. |
| Las reglas ESTE-018 y ESTE-024 dan órdenes distintos para condición y acción. | En procedimientos, advertencia primero y condición antes del mandato. |
| No hay una protección general explícita de literales técnicos. | SS-02 protege código, etiquetas publicadas, marcadores y otros literales. |
| Los casos de regresión usan fragmentos y algunos fijan una corrección incorrecta. | Las comprobaciones deben usar pasajes completos y requisitos de significado. |

### Simple English, de AminBlg

- [Skill consultada](https://github.com/AminBlg/SimpleEnglish/blob/a6fcb4fde098b33617cc1578d151ebf58774b883/skills/simple-english/SKILL.md).
- La copia instalada y el texto público consultado declaran la versión 2.1.1.
- [Licencia MIT](https://github.com/AminBlg/SimpleEnglish/blob/a6fcb4fde098b33617cc1578d151ebf58774b883/LICENSE), Copyright (c) 2026 AminBlg.

Simple English inspira una entrada breve, referencias por tipo de texto,
la protección de literales, la condición antes del mandato y una comprobación final.
Los avisos de ambas skills MIT se conservan en [LICENSE](../LICENSE).

No se trasladan sus prohibiciones generales de tiempos compuestos o de matices
como «might». No se convierten recomendaciones en obligaciones. Tampoco se
impone una sola palabra a conceptos distintos ni un formato de chat global.
La estructura sirve de referencia; las reglas de español se redactan para este proyecto.

## Otras guías de español claro y técnico

| Fuente primaria consultada | Uso en esta skill | Límite |
| --- | --- | --- |
| Comisión Europea, Dirección General de Traducción, [Cómo escribir con claridad](https://op.europa.eu/en/publication-detail/-/publication/725b7eb0-d92e-11e5-8fea-01aa75ed71a1/language-es), edición 2015, DOI 10.2782/259493. | Pensar en la tarea y el lector; usar términos consistentes, verbos concretos y sujetos solo cuando hagan falta; revisar con otra persona. | Consejos editoriales para varios tipos de documentos, no una norma de español técnico controlado. |
| Microsoft, [Spanish (Neutral) Style Guide](https://download.microsoft.com/download/4/3/1/431d9836-40dc-4f2b-aafc-def5c7b5d0f3/spa-neu-StyleGuide.pdf), apartados 2.2, 3.1, 5.1.16 y 6.3. | Considerar la región, respetar terminología y UI, conservar el subjuntivo necesario y prestar atención a marcadores. | Guía de localización de productos Microsoft. No se importan sus decisiones de marca, listas de sinónimos ni preferencias como reglas universales. |
| RAE/ASALE, DLE, entrada [actual](https://dle.rae.es/actual). | Admitir «actual» con el sentido de presente. | Una definición no elimina las ambigüedades de referencia de una frase concreta. |
| RAE/ASALE, DPD, entrada [gerundio](https://www.rae.es/dpd/gerundio), apartados 5, 6 y 7. | Distinguir acciones en curso, simultaneidad, posterioridad y consecuencia sin una prohibición mecánica del gerundio. | La aceptabilidad gramatical no demuestra que un procedimiento sea claro. |
| RAE, [presentación de la Guía panhispánica de lenguaje claro y accesible](https://www.rae.es/noticia/disponible-la-guia-panhispanica-de-lenguaje-claro-y-accesible), 28 de octubre de 2024. | Considerar comprensión, uso, ambigüedad y accesibilidad sin empobrecer la gramática. | Se consultó la presentación pública, no el libro completo. No se atribuyen al libro reglas que no se verificaron. |

Se leyó el PDF de la Comisión Europea. Son especialmente relevantes las
páginas impresas 3 a 9 y 14. En su página 6, las 20 palabras son una media
orientativa, no un límite absoluto. Su página 9 explica que el sujeto puede
omitirse en español cuando se entiende. El PDF permite reproducción con
indicación de la fuente; este proyecto no distribuye el PDF ni sus ilustraciones.

Los documentos de Microsoft y RAE se enlazan como referencias. No se incluyen
sus textos completos ni se presentan bajo la licencia MIT de este proyecto.

## Alcance de las afirmaciones

Los objetivos de longitud y los IDs SS son decisiones de este proyecto.
No se atribuyen como reglas literales de las fuentes anteriores.

ASD-STE100 es un referente de inglés técnico, no una norma de español.
Simple Spanish no reproduce su diccionario ni declara conformidad con él.
Tampoco declara conformidad con ISO 24495-1 o UNE 153101.
El lenguaje claro y la Lectura Fácil tienen alcances distintos.
Esta skill no sustituye una evaluación de accesibilidad ni una revisión del dominio.

## Contexto conceptual y evaluación de traducciones

El [catálogo de errores MQM](https://www.themqm.org/mqm-pillars/the-mqm-full-typology/)
distingue terminología incorrecta, relaciones técnicas alteradas y ambigüedad
introducida en la traducción. Se usa para concretar la revisión del significado
y del contexto. No se reproduce su catálogo completo ni se declara conformidad
o una puntuación MQM. Los ejemplos de traducción de esta skill son sintéticos;
sus equivalentes dependen del contexto y no forman un diccionario universal.
