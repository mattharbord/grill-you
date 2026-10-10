---
name: grill-you
description: Use when explicitly invoked to examine and refine the agent's understanding of a project. Explain the project's goals to a user-chosen audience, let the user question the explanation in that audience's voice, and absorb owner corrections marked with square brackets.
---

# Grill You

Explain your understanding of the user's project so the user can question it and correct it. Treat this as a conversation about what the project is trying to achieve. Start with the big picture and move into finer detail as the conversation leads there.

## Begin

Ask who you are explaining the project to and what that person knows outside this project, unless the user has already specified both. The listener has no prior project context. A developer, designer, quant, manager, child, or other listener can still have their own background knowledge. Ask which project or part of it is in scope only if the supplied context does not make that clear. Use the context and materials already available instead of asking the user to repeat them.

Then explain the project's purpose in your own words: what the user is trying to change, why, and the main consequences if it works. Begin at this level even if the supplied context is detailed. Keep the opening short enough to invite questions. Make uncertainty visible where the context does not support a confident account.

## Converse and revise

The user speaks as the chosen listener by default. Their unmarked questions and statements are probes of your understanding. Answer them as you would answer that listener. Let questions and prompts such as "explore this further" or "go deeper" set the path and depth. When the listener changes, explain the big picture again for the new audience while keeping what you learned about the project.

In the user's own prose, any square-bracketed passage is the project owner's voice. It does not need a `Me:` prefix. Text outside the brackets remains in the listener's voice. Treat brackets in code, Markdown links, quoted source material, or escaped literal text as content rather than a voice switch. Brackets establish who is speaking; a tentative idea or question inside them is not automatically a settled decision.

Route the speaker before interpreting intent or taking action. While this skill is active, unmarked prose remains listener speech even when it asks about the skill, describes a possible flaw, or asks what would happen if something changed. Answer those questions; do not infer an owner request to fix the flaw or edit files. If an unmarked statement appears to direct a change or correct your project understanding, clarify whether the owner meant to step out of role. Do not begin a change while waiting. Adopt project corrections only from bracketed owner statements or a direct confirmation after clarification. Edit files only on the owner's explicit request to edit them.

Apply owner corrections before answering listener questions from the same message. Briefly say how a material correction changed your understanding, then continue the explanation from the revised view. Revisit earlier conclusions if the correction affects them. An owner correction to your understanding does not, by itself, request a document edit.

Explain what the supplied context supports, what you infer from it, and what remains unknown, without turning every reply into a formal report. If materials conflict with an owner correction, identify the conflict when it matters. Do not fill a gap with a confident invention.

## End the session

A bracketed owner request to end `grill-you` or return to ordinary conversation ends the listener role. `[End grill-you]` is an example, not required wording. Give the brief closing account described below. Treat subsequent unmarked messages as the project owner's normal voice. If an unmarked message directly requests an exit, ask whether the owner intends to end the skill; a direct confirmation is enough. Answer unmarked questions about how to exit without treating them as exit requests.

## Keep the conversation useful

Maintain a small, provisional map of the main project themes and their immediate subtopics in the background. Track which themes have merely been explained, which the listener has explored, and which remain untouched or open. A theme is not explored merely because you mentioned it. Follow the user's chosen path. At a natural pause, surface one important untouched theme if it could change your understanding of the project. Keep the map out of ordinary replies unless the user asks to see it.

Use clear, audience-appropriate prose. Draw on Simplified Technical English principles such as consistent terms and short, direct sentences, but do not claim formal ASD-STE100 compliance. This is not an ELI5 exercise unless the chosen audience calls for that style. Usually answer in one to three short paragraphs; rarely exceed five unless the question warrants more detail. Avoid recurring checklists, mandatory examples, approval gates, and long recaps.

Keep an in-chat audit of material owner corrections and unresolved points through brief acknowledgments as they arise. When the user ends the session, give a concise account of your current understanding and any important themes still open or untouched. Save that account to a file only if the user requests it.
