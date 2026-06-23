# CLAUDE.md — `.github`

This is the organization's **community-health repo**. Its "code" is Markdown and
issue-form YAML, not an application — there is no stack, build, or test here.

## What this repo does (and its one big gotcha)

GitHub uses files here as **org-wide defaults** for repos that don't define their
own (issue/PR templates, `CONTRIBUTING`, etc.). Two things to keep straight:

- Inheritance is a **UI fallback, not a real file.** A default shows up in
  GitHub's web UI for repos lacking their own copy; it is **not** copied into
  those repos and is **not** present in their clones. Editing a file here does
  not change anything on disk in another repo.
- **Agent-instruction files don't inherit.** This `CLAUDE.md` only applies when
  working *inside this repo*. It does not reach other repos or their agents.

So changes here affect the *templates GitHub offers*, not other repos directly.

## Layout

- `PULL_REQUEST_TEMPLATE.md`, `CONTRIBUTING.md`, `README.md` — repo root.
- `.github/.github/ISSUE_TEMPLATE/` — issue forms (`*.yml`) + `config.yml`. The
  doubled `.github/.github/` path is intentional: GitHub reads templates from a
  `.github/` folder, and that folder lives inside a repo *named* `.github`.

## How the templates are consumed (design rationale)

- **Issue templates:** GitHub shows a **picker**, and `config.yml` sets
  `blank_issues_enabled: false`, so every issue is forced through one of
  Bug / Feature / Chore.
- **PR template:** GitHub gives PRs **no picker.** The root
  `PULL_REQUEST_TEMPLATE.md` auto-loads and is the *only* template most PRs ever
  see — `gh`/headless/agent PRs get it too (or nothing). There are intentionally
  no PR-template variants; keep the single root template self-sufficient.

## Editing issue forms

Each `*.yml` is a GitHub issue **form**: `name`, `description`, a `title` prefix,
`labels`, and a `body` of fields (`type: textarea | input | dropdown |
checkboxes`, each with `validations.required`). Keep them lean — they are
**prompts for a teammate logging work, not a form for an outside reporter.**
Almost nothing should be `required`; the team's workflow is deliberately
non-enforced.

## Conventions

- Base branch is **`master`** (Aspen convention — don't rename to `main`).
