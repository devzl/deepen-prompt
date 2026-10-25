# Deepen Prompt

**Deeper methods. Same scope. Then execute.**

Deepen Prompt improves how a task is done using primary sources, named
methods, and independent verification. It rewrites the prompt, then carries
it out without expanding scope.

**Official name:** `deepen-prompt`. **Shortcut:** `dpx`.

## What it does

Given a task or question, Deepen Prompt identifies:

1. The professional practices that would most improve the result.
2. The primary source material to start from.
3. Named methods and tools suited to the task.
4. An independent way to check the result.

It preserves project instructions and authorization boundaries, and reports
failed or unavailable checks. The canonical instructions are in
[SKILL.md](plugins/deepen-prompt/skills/deepen-prompt/SKILL.md).

## Use

Invoke the full name or its shortcut in a host that exposes skills as slash
commands:

```text
/deepen-prompt Investigate why our checkout conversion dropped last week.
/dpx Investigate why our checkout conversion dropped last week.
```

In hosts that use dollar-prefixed skills, use `$deepen-prompt` or `$dpx`.
For a host that namespaces plugin skills, the corresponding invocations are
`/deepen-prompt:deepen-prompt` and `/deepen-prompt:dpx`.

The shortcut is configured as a small
[alias skill](plugins/deepen-prompt/skills/dpx/SKILL.md) that loads the canonical
instructions. Both skills ship together; no separate `deepen-prompt`
installation is required.

## Install from this checkout

This repository follows [handover](https://github.com/devzl/handover)'s plugin
and marketplace layout. Run installation commands in your target host.

### Claude Code plugin

```text
/plugin marketplace add /absolute/path/to/deepen-prompt
/plugin install deepen-prompt@deepen-prompt
```

The plugin includes both `deepen-prompt` and `dpx` skills. If an existing
personal `/dpx` command takes precedence, use `/deepen-prompt:dpx` to select
the packaged shortcut explicitly.

### Manual skill installation

Copy both skill folders so the relative shortcut reference resolves.
For a project using `.agents/skills/`, run from that project's root:

```bash
mkdir -p .agents/skills
cp -R /absolute/path/to/deepen-prompt/plugins/deepen-prompt/skills/deepen-prompt .agents/skills/deepen-prompt
cp -R /absolute/path/to/deepen-prompt/plugins/deepen-prompt/skills/dpx .agents/skills/dpx
```

For a personal Claude Code installation:

```bash
mkdir -p ~/.claude/skills
cp -R /absolute/path/to/deepen-prompt/plugins/deepen-prompt/skills/deepen-prompt ~/.claude/skills/deepen-prompt
cp -R /absolute/path/to/deepen-prompt/plugins/deepen-prompt/skills/dpx ~/.claude/skills/dpx
```

### OpenAI Codex / Codex CLI

The repo ships a Codex marketplace (`.agents/plugins/marketplace.json`):

```bash
codex plugin marketplace add devzl/deepen-prompt
codex plugin add deepen-prompt@deepen-prompt
```

Or copy the skills directly (project `.codex/skills/` or global `~/.codex/skills/`):

```bash
mkdir -p ~/.codex/skills
cp -R /absolute/path/to/deepen-prompt/plugins/deepen-prompt/skills/deepen-prompt ~/.codex/skills/deepen-prompt
cp -R /absolute/path/to/deepen-prompt/plugins/deepen-prompt/skills/dpx ~/.codex/skills/dpx
```

### GitHub Copilot

Copilot CLI reads `.claude-plugin/marketplace.json` natively:

```bash
copilot plugin marketplace add devzl/deepen-prompt
copilot plugin install deepen-prompt@deepen-prompt
```

### Cursor

Cursor reads `.claude/skills/` and `.codex/skills/` for compatibility, so the
copies above work. Or install directly:

```bash
mkdir -p .cursor/skills
cp -R plugins/deepen-prompt/skills/deepen-prompt .cursor/skills/deepen-prompt
cp -R plugins/deepen-prompt/skills/dpx .cursor/skills/dpx
```

### Gemini CLI

Gemini CLI recognizes `.agents/skills/`, which this repo provides:

```bash
gemini skills install https://github.com/devzl/deepen-prompt
```

Or copy into `.gemini/skills/` (project) or `~/.gemini/skills/` (global):

```bash
mkdir -p .gemini/skills
cp -R plugins/deepen-prompt/skills/deepen-prompt .gemini/skills/deepen-prompt
cp -R plugins/deepen-prompt/skills/dpx .gemini/skills/dpx
```

### OpenCode

OpenCode discovers `SKILL.md` in `.agents/skills/`, `.claude/skills/` and
`.opencode/skills/`. Point it at this repo, or copy:

```bash
mkdir -p .opencode/skills
cp -R plugins/deepen-prompt/skills/deepen-prompt .opencode/skills/deepen-prompt
cp -R plugins/deepen-prompt/skills/dpx .opencode/skills/dpx
```

### Kiro

Import from the repo URL (Kiro -> Import a skill), or copy into `.kiro/skills/`
(project) or `~/.kiro/skills/` (global):

```bash
mkdir -p .kiro/skills
cp -R plugins/deepen-prompt/skills/deepen-prompt .kiro/skills/deepen-prompt
cp -R plugins/deepen-prompt/skills/dpx .kiro/skills/dpx
```

### Windsurf

Windsurf uses the same `.agents/skills/` convention, or copy both skill
folders into the skills directory your setup scans.

### Any other Agent Skills host

Copy both folders from `plugins/deepen-prompt/skills/` into the directory your
tool scans for `SKILL.md`. With no skills support, paste the body of
[SKILL.md](plugins/deepen-prompt/skills/deepen-prompt/SKILL.md) (below the
frontmatter) into your prompt.

## Repository layout

```text
.claude-plugin/marketplace.json
.agents/plugins/marketplace.json
.agents/skills/deepen-prompt -> canonical skill (symlink)
.agents/skills/dpx           -> shortcut skill (symlink)
plugins/deepen-prompt/
  plugin.json
  .claude-plugin/plugin.json
  .codex-plugin/plugin.json
  skills/deepen-prompt/SKILL.md
  skills/dpx/SKILL.md
```

The manifests follow handover's structure. Installation support varies by
host; the manual skill copy is available independently of marketplace support.

## License

MIT. See [LICENSE](LICENSE).
