# Routing Matrix

Use this reference when choosing between shell, MCP, skills, and web is not obvious.

## Quick Matrix

### Local file inspection

Choose this when:

- the answer likely exists in repo files
- the task is code reading, config reading, or diff inspection
- no external state is needed

### Shell

Choose this when:

- the task is command-line native
- the output comes from git, rg, build tools, package managers, or scripts
- the work is faster as a command than as manual reasoning

### MCP or app tools

Choose this when:

- the task depends on Unity editor state
- screenshots, play mode, scene hierarchy, or structured editor APIs matter
- the app has a first-class tool that is safer than raw shell

### Web

Choose this when:

- the user explicitly asks for lookup or verification
- the fact may have changed recently
- a primary external document or page is required

### Skill-first

Choose this when:

- the main challenge is process discipline
- there is already a skill designed for this exact class of task
- choosing a tool before choosing the workflow would create drift

## Example Decisions

- compare two UI recordings: use the `eye-runtime-capture-compare` skill, then use local files or media tooling as needed
- inspect Unity scene wiring: use MCP scene or hierarchy tools, not generic shell
- verify a current API policy: use web with official sources
- prepare a cross-window continuation: use `memory-codex-handoff`, not raw status compression
