#### Co-pilot custom chat modes

This project is to discover the best way to instruct GitHub Copilot using custom prompt files. session, repository, directory, and file-level instructions.

https://copilotthatjawn.com/tips/copilot-instructions-prompt-files.md

The .github/copilot-instructions.md file enforces project standards and conventions.

The .chatmode.md instructs how the assistant should communicate or think — e.g., “be structured”, “generate step-by-step plans”, or “focus on trade-offs”.

Both are merged into the model’s prompt. The chat mode shapes dialog context; the instructions anchor stable project behavior.​

Each works best when your instruction file specifies static do-and-don’t rules and your ChatMode file defines dynamic reasoning style and task pattern.

ChatMode files (.chatmode.md / .prompt.md) define session intent, personality, and interaction focus (e.g., “act as a reviewer,” “use structured reasoning”).

Repository-level instructions (.github/copilot-instructions.md) enforce project-wide standards like frameworks, code quality targets, formatting, or architecture rules.​

Directory or file-level .instructions.md files refine those rules for specific technologies or submodules, often using YAML frontmatter like applyTo: "lib/**/*.dart".​

Together they ensure that what Copilot says (chat mode context) always aligns with what it produces (code standards from instruction files).

Example balanced configuration:

.github/copilot-instructions.md – project-wide coding standards

/frontend/ui.instructions.md – specific to Tailwind + React components

/backend/api.instructions.md – Spring Boot conventions

/chatmodes/Architect.chatmode.md – reasoning persona for architectural queries

When these are used together, Copilot consistently outputs code matching your conventions, while maintaining mode-specific communication tone and reasoning depth.

In summary, the layered combination method—session + repo + path-level—is the most effective configuration. It turns Copilot into a coherent assistant capable of applying both global project standards and task-specific reasoning behavior in real time