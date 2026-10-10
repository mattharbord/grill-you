# `grill-you` draft: design decisions and experiments

Draft date: 2026-10-10. The skill source is [SKILL.md](SKILL.md). This is a first draft for discussion and testing, not a claim that the conversation pattern has been validated in use.

## Intent retained from the discussion

- The agent explains what it understands the project to be trying to achieve. The user questions it as a chosen listener with no prior project context.
- The explanation begins with project goals and high-level consequences, then follows the conversation into detail. The listener can have relevant professional knowledge.
- Unmarked user prose is in the listener's voice. A square-bracketed passage in user prose is the project owner's voice; `Me:` is unnecessary. Apparent unmarked corrections are clarified before they change the project model.
- The agent routes the speaker before interpreting intent or taking action. A listener's question about a flaw does not authorize an edit; ambiguous unmarked corrections or commands are clarified before any change begins.
- A bracketed owner request ends the listener role and restores ordinary user voice for later messages. A direct unmarked exit request is clarified before the switch; a question about how to exit is answered as a listener question.
- The skill is invoked explicitly. Onboarding asks who the listener is and what they already know outside the project.
- The agent keeps a coverage map in the background, brings up consequential untouched themes at natural pauses, and keeps a light in-chat record of material corrections and unresolved points.
- Replies stay conversational and succinct: normally one to three short paragraphs, rarely more than five unless the question needs it. Writing is STE-inspired rather than formally ASD-STE100 compliant.

## Choices made where other directions were plausible

| Choice in this draft | Alternative considered | Reason and trade-off |
| --- | --- | --- |
| A self-contained `SKILL.md` | A short wrapper that invokes Matt Pocock's `grilling` skill | The proposed roles and pacing differ from `grilling`, and a named-skill call can depend on the host. Self-containment duplicates a little conceptual ground but avoids a fragile dependency. |
| Explicit invocation via `agents/openai.yaml` | Automatic activation after a large context handoff | The user chose explicit invocation because the audience question and conversational mode should begin deliberately. |
| A background coverage map | A displayed topic checklist or no map | The user wanted awareness of neglected high-level areas while keeping each turn conversational. A hidden map is less burdensome but makes its quality harder to inspect. The user can ask to see it. |
| Square brackets for owner prose | Requiring `[Me: ...]` or separate owner/persona messages | Any bracketed prose matches the user's natural editorial habit and allows mixed voices in one message. Code, links, quoted material, and escaped literal text are treated as content to avoid false switches. |
| Voice routing before action | Treating a question about a gap as a request to fix it | The first live test exposed this failure: an unmarked question about ending the skill prompted an unauthorized draft edit. The agent must answer listener questions and clarify ambiguous commands before changing files or confirmed understanding. |
| Bracketed exit request, with no fixed phrase | A single required exit command or automatic timeout | The owner already has a voice channel. `[End grill-you]` is easy to remember, while other clear owner requests can work. Unmarked exit commands are confirmed because the listener remains the default voice. |
| In-chat correction audit, optional file on request | A file updated after every answer | This keeps the exchange light. Long sessions could still benefit from an explicit export or checkpoint. |
| STE-inspired prose | Formal ASD-STE100 compliance | The standard's controlled vocabulary and rules would add a validation task and could restrict audience-specific language. The draft asks for clarity without claiming compliance. |
| Natural depth changes | A fixed level-by-level script | The user wants to explore in the listener's voice. The agent retains the top-level map so a deep branch does not hide major untouched areas. |
| Brief acknowledgment after material corrections | A visible change log after every turn | The audit should expose revisions without repeatedly interrupting the conversation. |
| No mandatory scenario or consequence example per branch | A formal test of each claimed understanding | The user found this too prescriptive for product-level discussion. The agent can use examples when a question benefits from one. |
| No per-branch sign-off | Explicit approval before descending | The conversation should flow naturally. The closing account identifies open and untouched themes without claiming every detail was approved. |

## Deliberately left out

- No scripts, scoring, alignment percentage, or rigid state machine. The workflow depends on conversational judgment.
- No required project artifact, code change, or technical design output. The product of this skill is the clarified conversation; an export is available on request.
- No fixed list of generic topics. The map should come from the actual project context and change when the owner's understanding changes.
- No dependency on `grill-me` or `grilling`. The two skills can complement each other without either being installed for this draft to work.

## Worth testing in a first run

1. Give the agent a long, jargon-heavy product brief. Check whether its opening stays short, starts with purpose, and uses fresh language.
2. Mix persona questions with an owner correction in `[brackets]`. Check whether the correction changes the explanation before the persona question is answered.
3. Put code such as `items[0]`, a Markdown link, and a quoted bracketed statement in the user's message. Check that none is treated as owner speech.
4. Give an unmarked statement that sounds like a project correction. Check that the agent flags the ambiguity without silently adopting it or demanding that the user retype it.
5. Spend several turns on one branch. Check whether the agent eventually surfaces one material untouched theme at a natural pause without dumping a checklist.
6. Switch from a developer listener to a sales listener. Check that the agent changes its explanation while preserving confirmed project understanding.
7. End with unresolved areas. Check that the closing account is brief and does not imply those areas were approved.
8. Ask an unmarked meta question that exposes a gap, such as how to exit. Check that the agent answers without editing files. Then exit with `[End grill-you]` and check that the next unmarked message is treated as ordinary owner speech.

The hardest behavior to judge from the text alone is the background map: whether the agent notices a genuinely important untouched theme without interrupting a useful discussion. A real run should settle whether this instruction needs tightening or whether it is already sufficient.
