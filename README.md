# no-slop — AI writing skills for clear, natural prose

Six open-source writing and editing skills for **Claude Code, Codex and other Agent Skills-compatible assistants**. Remove AI slop, vague claims, canned transitions and unnecessary words while preserving facts, qualifications and the writer's meaning.

[![Download](https://img.shields.io/github/v/release/kvngnsn/no-slop?label=download)](https://github.com/kvngnsn/no-slop/releases/latest) [![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE) [![Agent Skills](https://img.shields.io/badge/Agent%20Skills-portable-2d6a4f)](https://agentskills.io/specification)
[![Checks](https://github.com/kvngnsn/no-slop/actions/workflows/check.yml/badge.svg)](https://github.com/kvngnsn/no-slop/actions/workflows/check.yml)

**Start here:** [install](#install) · [choose a skill](#choose-a-skill) · [examples](#what-changes) · [download ZIPs](https://github.com/kvngnsn/no-slop/releases/latest)

Formerly **Wording**. The default editing skill is now `no-slop`; the five other writing modes use the `no-slop-` prefix.

## What changes

| Before | After |
|---|---|
| “We leverage a robust framework to facilitate seamless collaboration.” | “The team edits the same document together.” *Use only if that feature is supported.* |
| “The small pilot could facilitate a reduction in waiting time, although the limited sample does not permit confident generalization.” | “The small pilot may reduce waiting time, but the limited sample does not show whether it would help elsewhere.” |
| “I am reaching out to explore potential synergies.” | “Could we meet for 15 minutes to discuss the prototype?” *Use only when that is the actual request.* |

These illustrate the editing approach, not measured model results. The aim is clearer meaning and appropriate voice, without inventing evidence or erasing uncertainty. This is not an AI-detector bypass tool.

## Install

### Claude Code and Codex

Requires Python 3.9+ for the installer; the writing instructions themselves are plain Markdown.

```sh
git clone https://github.com/kvngnsn/no-slop.git
cd no-slop
python3 tools/skills.py install --scope user --apply
```

This installs all six skills as links in `~/.claude/skills` and `~/.agents/skills`. Keep this checkout in place. Existing unrelated files are never overwritten. Open a new session after installing.

- Add `--provider claude` or `--provider codex` to install for one host.
- Omit `--scope user` for project-only installation; those links survive moving the project.
- Add `--copy` for independent copies instead of links. Copies need separate updates.
- Omit `--apply` to preview the install without changes.

**Claude Code:** `/no-slop Rewrite this draft clearly. Preserve every fact and qualification: …`

**Codex:** `$no-slop Rewrite this draft clearly. Preserve every fact and qualification: …`

### Upload or use another model

The [latest release](https://github.com/kvngnsn/no-slop/releases/latest) includes a full pack ZIP and six individual skill ZIPs. For hosts that import one skill at a time, upload the corresponding individual ZIP. For a manual setup, give your assistant the relevant `skills/<name>/SKILL.md` file. A capable local-model agent can use the same instructions; available tools and model quality still matter.

To build upload archives yourself:

```sh
python3 tools/skills.py package --output packages
```

See the [open Agent Skills format](https://agentskills.io/specification) and your host's current skill-import instructions. No provider API key or hosted service is required by this pack.

## Choose a skill

| Skill | Job | Typical use |
|---|---|---|
| [no-slop](skills/no-slop/SKILL.md) | Edit a draft | Clarity, concision, structure and voice |
| [no-slop-explain](skills/no-slop-explain/SKILL.md) | Explain | Articles, FAQs and technical explanations |
| [no-slop-persuade](skills/no-slop-persuade/SKILL.md) | Make a case | Proposals, pitches, advocacy and copywriting |
| [no-slop-analyze](skills/no-slop-analyze/SKILL.md) | Weigh evidence | Research synthesis, comparisons and recommendations |
| [no-slop-instruct](skills/no-slop-instruct/SKILL.md) | Teach a procedure | Tutorials, onboarding and documentation |
| [no-slop-correspond](skills/no-slop-correspond/SKILL.md) | Write to someone | Email, outreach, requests and follow-ups |

Choose one primary mode. Each skill is self-contained. Useful context: reader, purpose, source facts, required length/format and a voice sample when relevant.

## Why six modes?

An explanation helps someone understand; a proposal supports a decision; instructions help someone complete a task. A single generic “make this better” prompt does not define success for all three.

Each skill chooses structure for the reader's job, develops supported points and checks the finished writing against the source. Plain language does not mean deleting technical detail or forcing every sentence to be short. The pack follows [plain-language principles](https://www.archives.gov/open/plain-writing/10-principles.html) and preserves the user's requested genre, voice and evidence limits.

A drafting request does not authorize sending, publishing or making commitments. The pack does not verify sources it cannot access, promise detector scores or establish a universally best style.

## Updating from Wording

GitHub redirects the old repository URL. Update your remote with `git remote set-url origin https://github.com/kvngnsn/no-slop.git`, pull, then run the installer again. `wording-edit` becomes `no-slop`; the other five names change from `wording-…` to `no-slop-…`. Remove an old installed entry only after confirming it belongs to Wording; do not delete unrelated skills or locally modified copies. Old release archives remain available as historical versions.

## Checks and contributions

```sh
python3 tools/skills.py validate
python3 -m unittest discover -s tools -p 'test_*.py'
```

The checks cover metadata, installation collisions, relocation and ZIP integrity; they do not measure writing quality. For an improvement, include a fictional or public before/after example, explain what meaning must survive, and describe the observed failure. Keep private drafts out of issues and pull requests.

[MIT license](LICENSE).

## Related open-source skills

| Project | Use it for |
|---|---|
| [click-everything](https://github.com/kvngnsn/click-everything) | Exploratory UI testing, reproducible bugs and regression tests. |
| [startupassist](https://github.com/kvngnsn/startupassist) | Startup legal documents, founder equity and financing templates. |
| [patentassist](https://github.com/kvngnsn/patentassist) | Invention intake, prior-art research and patent application drafting. |
