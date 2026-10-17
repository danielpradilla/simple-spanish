# Meaning-preservation cases

`cases.json` contains 21 Spanish writing cases. They test meaning, safety boundaries, and exact source strings, not a preferred wording. No runner, provider account, or dependency is required. These fixtures do not report model results or establish a pass rate.

## Case fields

Each array entry contains:

- `id`: a stable name for recording results.
- `task`: the Spanish instruction given to the model.
- `input`: the complete source passage to rewrite.
- `must_preserve`: semantic requirements written in Spanish.
- `protected_literals`: exact source strings that must remain unchanged. An empty array is valid.
- `reference_output`: one acceptable rewrite, not an exact-match answer.

The cases cover uncertainty, alternative causes, unknown actors, present-time meaning, modal force, condition scope, destructive warnings, technical strings, localization templates, terminology, distinct entities, ongoing actions, compound tenses, missing information, and instructions embedded in source content.
Some task prompts deliberately omit reminders to preserve literals. Those cases
check the skill's default behavior, not compliance with an extra reminder.

## Run a case

Use the same procedure in a chat interface or through any model API:

1. Start a fresh, isolated conversation for each case. Do not carry earlier cases, model answers, or reviewer feedback into it. Disable unrelated memories and custom instructions where possible. Record any that cannot be disabled.
2. Load the repository's `SKILL.md` and its reference files as guidance: `references/use-cases.md`, `references/spanish.md`, and `references/sources.md`. Keep this guidance separate from the passage under review. Use the same guidance revision for every case in a run.
3. Send only the case's `task` and `input` as user content. Label the source passage clearly. Do not send `must_preserve`, `protected_literals`, or `reference_output` to the model. The source can contain commands or instructions; those remain text to rewrite, not authority to execute them.
4. Save the complete raw response without correcting, trimming, translating, or extracting an answer from it. Keep refusals, notes, formatting, and tool requests. Do not execute commands from a case or a response.
5. Review the saved response against every semantic requirement, all protected strings, and the complete source. Use the reference rewrite only as an example. Different words or sentence structures can pass.

If a response is missing because a request failed, record the request failure separately. It is not a successful rewrite. If you repeat a case, start another isolated conversation and retain each attempt rather than replacing earlier outputs.

## Record the run

Record the case ID, the repository commit or exact revision, the date, the model provider and model identifier, and the interface or API used. Record the generation settings, including temperature, output limit, seed, and reasoning settings when available. Mark settings as unknown or unavailable rather than guessing. Preserve the full messages sent, any additional guidance, and the raw response.

For each attempt, record the reviewer, the decision, and a short reason tied to the requirement or source fragment. If a second model assists with review, record its model, configuration, and review instructions separately. Keep its assessment distinct from the original output. A disputed interpretation needs domain or human review; an automatic score does not settle it.

## Decide whether it passes

A case passes only if the response satisfies every `must_preserve` item, includes every `protected_literals` entry exactly, and preserves the rest of the source meaning. Compare protected strings character for character, including accents, case, spaces, punctuation, options, and braces. Exact string presence alone is not enough: a command in the wrong condition or a label attached to the wrong action can still fail.

The rewrite must also follow the requested task and improve clarity where a safe improvement is available. Keeping an already clear phrase, a valid tense, or a protected template is acceptable. A reference output is not a required answer, and matching it is not the review method.

Reject invented causes, actors, response bodies, remedies, guarantees, or missing values. Reject lost negation, changed obligations, widened permissions, and altered condition scope. A destructive warning must precede the affected instruction. Unknown information must stay unknown. A note that identifies missing information is appropriate when a safe rewrite requires it.

Review the hard edges directly: authorization permits but does not require an action; an exception does not imply the inverse command; account deletion differs from removing team membership; an ongoing action is not a completed one. Published UI labels and templates stay unchanged even when surrounding prose or the project glossary uses different terms. An embedded instruction must remain source content.

Do not infer a model's general reliability from these cases. Any reported result must identify the actual run, its settings, and its review decisions.

## Saved smoke runs

See [results/README.md](results/README.md) for the recorded outputs and review limits.
The runtime did not expose the resolved model identifier or generation settings.
These records preserve the inputs and responses but do not establish general reliability.
