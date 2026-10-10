# grill-you

`grill-you` is a Codex skill for checking an assistant's understanding of a project through conversation. The assistant explains the project in its own words to a chosen listener with no prior project context. The user questions that explanation and can correct the assistant as the project owner.

It is a self-contained complement to [Matt Pocock's `grill-me`](https://github.com/mattpocock/skills), which asks the user for decisions. `grill-you` asks the assistant to show what it thinks the project is trying to achieve.

## Use

Invoke `$grill-you` and name the listener and their background, for example: “Explain this project to a product manager who uses AI tools but has not seen the project brief.” The skill asks for those details if they are missing.

Then ask questions as that listener. Unmarked messages stay in the listener's voice. Put project-owner corrections or directions in square brackets, such as `[The main goal is to reduce setup time, not add features.]`. If an unmarked statement sounds like a correction, the assistant asks which voice you intended before adopting it.

The assistant begins with the project's purpose and consequences, then follows your questions into detail. It keeps track of important themes that have not been explored. An owner correction updates its understanding in the conversation; editing a document requires a separate owner request.

To leave the listener role, say `[End grill-you]` or make another clear bracketed request to return to normal conversation. The assistant gives a brief account of its understanding and open areas, then treats later unmarked messages as your normal voice.

## Install

Place `SKILL.md`, `agents/openai.yaml`, and `LICENSE` in a `grill-you` directory under your Codex skills directory (`$CODEX_HOME/skills/grill-you/`). The skill is set for explicit invocation.

See [design notes](DESIGN_NOTES.md) for the choices behind the conversation format and areas to test in longer projects.

## License

[MIT](LICENSE) © 2026 mattharbord.
