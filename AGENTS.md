# Repository Guidelines

## Project Structure & Module Organization

This repository contains a small Streamlit application for Japanese AI writing tools.

- `app.py` is the main application and currently holds UI setup, prompt builders, tool definitions, and Gemini API calls.
- `requirements.txt` lists runtime dependencies.
- `.streamlit/config.toml` stores Streamlit server, browser, and theme settings.
- There is no dedicated `tests/` directory yet. Add one when introducing automated tests.

Keep new source modules close to the app until the code justifies splitting. For example, move prompt-building helpers into `prompts.py` only if `app.py` becomes hard to navigate.

## Build, Test, and Development Commands

Create and activate a virtual environment before installing dependencies:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Run the app locally with:

```bash
streamlit run app.py
```

Set `GEMINI_API_KEY` in your shell or enter the key in the Streamlit sidebar. Do not commit API keys or local secrets.

## Coding Style & Naming Conventions

Use Python 3 style with 4-space indentation, type hints for public helpers, and descriptive function names. Prompt builder functions should follow the existing `build_<tool>_prompt` naming pattern and accept `dict[str, str]`. Keep user-facing Japanese copy natural and consistent with the current tone.

Prefer small, explicit helper functions over large inline blocks. Preserve UTF-8 encoding because the application contains Japanese prompt text.

## Testing Guidelines

No automated test framework is configured yet. When adding tests, prefer `pytest` and place files under `tests/`, using names like `test_prompts.py`. Start with pure prompt-builder tests because they do not require Streamlit or Gemini network calls.

Before submitting changes, at minimum run:

```bash
python -m compileall app.py
streamlit run app.py
```

Manually verify the affected tool flow in the browser.

## Commit & Pull Request Guidelines

This directory does not include Git history, so no existing commit convention is available. Use short imperative commit messages, such as `Add SEO prompt validation` or `Refine sidebar API key help`.

Pull requests should include a clear summary, manual test notes, screenshots for UI changes, and any configuration or dependency changes. Link related issues when available.

## Security & Configuration Tips

Keep secrets out of the repository. Store API keys in environment variables or Streamlit session input only. Review dependency changes carefully because this app sends user-provided text to an external Gemini API.
