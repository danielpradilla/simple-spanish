# Saved model smoke runs

These are synthetic writing checks, not a reader study or a reliability benchmark.
The implementing assistant reviewed each saved response against the source and
semantic requirements. Exact protected strings were also checked programmatically.
Reference outputs were not included in generation prompts.

| Saved run | Guidance revision | Corpus requests | Other requests | Responses rejected in this review |
| --- | --- | ---: | ---: | ---: |
| [0.1.0](2026-10-17-v0.1.0.json) | `d9d2a2f` | 19 | 2 | 0 |
| [0.1.1](2026-10-17-v0.1.1.json) | `e1bac76` | 21 | 2 | 0 |
| [0.1.1 generic-prompt follow-up](2026-10-17-generic-prompts.json) | `e1bac76` | 3 | 0 | 0 |

The versions use different case sets. These counts do not measure improvement
between versions. The other requests exercise review output and new UI copy.
The earlier run remains unchanged as a record of that revision.
The follow-up removes preservation reminders from three task prompts. The other
18 tasks and all skill guidance are unchanged from the full 0.1.1 run.
Their outputs were not regenerated. The full run and follow-up together cover
the current corpus.

## Inputs and review

Each JSON record contains the full user messages, unchanged raw responses,
guidance-file hashes, a pinned commit, the exact system-message construction,
and a per-response review decision. The guidance files at `guidance_revision`
reconstruct the system message. The corpus at `case_revision`, or at
`guidance_revision` when no separate case revision is recorded, supplies the requirements.
One stateless request was used for each input. The generation interface supplied
no tools or conversation history.

All saved requests used the runtime's `default` model alias. The completion interface did
not expose the resolved provider, model identifier, temperature, output limit,
seed, or reasoning settings. These values are recorded as unavailable, not inferred.
The input messages can be reconstructed, but these records do not support an
exact model rerun or a comparison across models.

## Limits

The reviewer of these outputs was the implementing assistant, not an independent
human reader. Independent agent review checked the skill's instructions and examples;
it did not establish reader comprehension or production safety.
These results do not prove that another request, model, or run preserves meaning.
Review safety-critical, legal, and other consequential text with a domain expert.
No commands included in the source passages were executed.

## Línea base de traducción con modelo identificado

[Registro de doce traducciones](2026-10-17-translation-baseline.json).
Usa la guía v0.1.1 de `feef2aa2152e71f073254a1fba8947ae86b7d806`,
Claude Code 2.1.302 y el modelo resuelto `claude-sonnet-5-5`, con esfuerzo `medium`.
Cada caso se ejecutó en un proceso nuevo, sin herramientas, MCP, persistencia
de sesión ni personalizaciones del cliente. Se conservan las respuestas crudas,
las instrucciones completas y las opciones no expuestas como no disponibles.
Los doce casos conservan los literales protegidos en esta ejecución.
Esto no es una aprobación semántica ni una medición de comprensión humana.
Los registros históricos anteriores no se sustituyen.

El identificador `unlimited-company` se hizo explícito en la fuente del corpus
después de esta línea base. El registro conserva la entrada original, que podía
leerse como una descripción traducible del plan. No compares su respuesta con
una entrada posterior distinta. Las comparaciones nuevas deben usar la misma
revisión del corpus en ambas ramas.
