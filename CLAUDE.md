# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A film-watching log for Sophie and Shreshth, backed by the [FilmStruck CLI](https://github.com/shreshthkhilani/filmstruck). The CLI manages film data and generates `index.html`, which is then deployed to GitHub Pages.

## How it works

Film data is managed entirely through the FilmStruck CLI (a .NET global tool). The CLI reads `filmstruck.json` for configuration and generates `index.html` as its output.

**`filmstruck.json`** — CLI config:
```json
{ "username": "s4s", "siteTitle": "filmstruck" }
```

**Common CLI commands** (requires `dotnet tool install --global FilmStruck.Cli`):
- `filmstruck build` — regenerates `index.html` from stored film data
- `filmstruck add` — add a new film entry
- `filmstruck list` — list tracked films

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which installs the FilmStruck CLI, runs `filmstruck build`, and deploys `index.html` + `favicon.png` to GitHub Pages at `https://shreshthkhilani.github.io/s4s-filmstruck/`.

## Key files

- `filmstruck.json` — CLI configuration (username, site title)
- `index.html` — **generated file**, do not hand-edit; regenerate with `filmstruck build`
- `favicon.png` — site icon, copied into deployment as-is
