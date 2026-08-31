# GOAR

Autonomous CLI coding agent. Provider-agnostic. Local-first.

```
  ██████╗  ██████╗  █████╗ ██████╗
 ██╔════╝ ██╔═══██╗██╔══██╗██╔══██╗
 ██║  ███╗██║   ██║██████║██████╔╝
 ██║   ██║██║   ██║██╔══██║██╔══██╗
 ╚██████╔╝╚██████╔╝██║  ██║██║  ██║
  ╚═════╝  ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝
```

[![PyPI version](https://img.shields.io/pypi/v/goar.svg)](https://pypi.org/project/goar/)
[![Python 3.12+](https://img.shields.io/badge/python-3.12%2B-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-Apache%202.0-green.svg)](https://github.com/goarxyz/goar-cli/blob/main/LICENSE)

GOAR reads your repo, runs tools, edits files, and finishes the task. It talks to any OpenAI-compatible endpoint plus Anthropic’s native Claude API. No vendor lock-in. No telemetry service.

## Install

Requires Python 3.12+.

```bash
pip install goar
```

With [uv](https://docs.astral.sh/uv/):

```bash
uv tool install goar
# or
uv pip install goar
```

From a local checkout:

```bash
pip install .
# or, editable
pip install -e .
```

Then:

```bash
goar
```

## First run

First launch opens the provider wizard. Re-run it anytime:

```bash
goar --setup
```

Supported providers:

| Key | API |
|---|---|
| `openai` | Official OpenAI |
| `anthropic` | Claude (native Messages API) |
| `openrouter` | Claude / GPT / Gemini / others through one key |
| `groq` | Groq OpenAI-compat |
| `together` | Together AI |
| `fireworks` | Fireworks AI |
| `nvidia` | NVIDIA NIM |
| `azure` | Azure OpenAI (you supply the resource URL) |
| `cursor` | Any Cursor-compatible OpenAI endpoint (you supply the URL) |
| `ollama` | Local `http://127.0.0.1:11434/v1` |
| `llamacpp` | Local `http://127.0.0.1:8080/v1` |
| `custom` | Any other OpenAI-compatible host |

Keys are written to `~/.goar/.env` (mode 0600). Config is written to `~/.goar/config.toml`.

## Usage

```bash
goar                          # interactive TUI
goar "fix the failing tests"  # start with a prompt
goar --setup                  # provider wizard
goar -p "summarize this repo" --agent auto-approve
```

Slash commands inside the TUI: `/help` `/model` `/setup` `/theme` `/config`.

Default theme is `goar-dark`. `/theme` also lists `goar-light` plus Textual builtins.

## Layout

```
~/.goar/
  config.toml
  .env
  logs/
  skills/
  agents/
  tools/
```

Project-local overrides: `.goar/config.toml`, `AGENTS.md`.

## Privacy

GOAR ships without telemetry, identity, experiment, and console-auth modules. Runtime traffic goes only to the model provider you configure.

## License

Apache-2.0. See `LICENSE` and `NOTICE`.

Derived from [Mistral Vibe](https://github.com/mistralai/mistral-vibe). Mistral, Vibe, and related marks are trademarks of their respective owners.

## Brand

Palette: ink `#0B0D10`, bone `#E8E4D9`, amber `#E8B84A`.
Logo assets: `assets/logo.svg`, `assets/logo.png`.
