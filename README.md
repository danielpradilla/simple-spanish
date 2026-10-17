# Simple Spanish

An agent skill for clear Spanish technical writing. It rewrites documentation,
procedures, UI text, errors, and agent instructions without changing their meaning.

Inspired by [ESTE](https://github.com/esadrian/este-skill) and
[Simple English](https://github.com/AminBlg/SimpleEnglish). This project adapts
their useful patterns and addresses findings from an adoption review.
It is an independent project, not an official release of either skill.

## Install and use

For an agent that supports the skills CLI:

```sh
npx skills add danielpradilla/simple-spanish
```

You can also copy this repository into your agent's skill directory under
`simple-spanish/`. Keep `SKILL.md` and its relative reference folders together.
This skill has no runtime dependencies, executable hooks, or bundled installer.
The skills CLI is a separate tool.

Example requests:

```text
Reescribe este procedimiento con simple-spanish.
Revisa este mensaje de error sin añadir causas ni soluciones.
Simplifica esta documentación. Conserva los comandos y las etiquetas publicadas.
```

The skill follows the requested output format. A rewrite returns the revised
text alone, unless an unresolved ambiguity needs a short note.
A review reports the problem, original passage, rule ID, and a safe correction.
It does not apply to unrelated conversation or change your agent settings.

## Rules that protect meaning

- Keep facts, uncertainty, negation, requirements, permissions, conditions, and exceptions.
- Keep code, commands, placeholders, paths, quoted errors, and published UI labels unchanged.
- Put warnings before the affected action and conditions before commands.
- Do not invent actors, causes, response fields, recovery steps, or guarantees.
- Keep domain distinctions such as user versus account, or membership removal versus deletion.
- Use natural Spanish, including valid gerunds, the subjunctive, and meaningful compound tenses.

Sentence-length targets are editing aids, not compliance tests.
The project does not use automatic word replacement or a universal Spanish dictionary.

## Example

Original:

> Se recomienda que active las alertas. Si así lo desea, puede desactivar los avisos por correo.

Revision:

> Se recomienda activar las alertas. Si lo desea, puede desactivar los avisos por correo.

The recommendation remains a recommendation. Disabling email notices remains optional.
See [more examples](examples/before-after.md) for API uncertainty, destructive
commands, unknown actors, and existing UI labels.

## Sources and design choices

The [source record](references/sources.md) links the exact ESTE and Simple English
revisions reviewed. It records what this project adapts and what it changes.
It also explains the source and review limits.

Other sources include the European Commission's Spanish clarity guide,
Microsoft's neutral Spanish localization guide, and RAE/ASALE references.
These sources inform the skill. They do not endorse it.

## Regression cases

[evals/cases.json](evals/cases.json) contains 21 complete writing cases.
Each case records the meaning and exact strings that must survive a rewrite.
Reference outputs are examples, not exact-match answers.
The [evaluation guide](evals/README.md) explains how to run and review them
with any model. Semantic review is required; string matching alone is not enough.
The separate [translation corpus](evals/translation-cases.json) adds 12 synthetic
English-to-Spanish cases with contrasting technical meanings. It checks concepts
and operational effects, not a universal dictionary of word replacements.
The [document corpus](evals/document-cases.json) adds two multi-section examples
for distributed context, cross-references, code, and documentary diagrams.
Saved [smoke responses and review limits](evals/results/README.md) are available.
They are not a reader study or a reliability benchmark.
A [reader pilot](evals/reader-study.md) includes passages, tasks, and answer keys.
It has no participant results.

## Scope and limits

Use this skill for technical and factual prose, not creative writing or marketing.
It does not guarantee a single interpretation, reader comprehension, or safe
operation. A person who knows the domain must review safety-critical text.

This project does not claim compliance with ASD-STE100, ISO 24495-1,
UNE 153101, or Lectura Fácil requirements. It includes no standards dictionary.
An English rule is not automatically a valid Spanish rule.

## License

[MIT](LICENSE). The license retains the notices for esadrian and AminBlg.
The linked external guides keep their own terms. Their full texts are not bundled.
