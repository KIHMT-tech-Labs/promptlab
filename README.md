# PromptLab

[![PromptLab Tests](https://github.com/KIHMT-tech-Labs/promptlab/actions/workflows/tests.yml/badge.svg)](https://github.com/KIHMT-tech-Labs/promptlab/actions/workflows/tests.yml)

A small, local-first toolkit for developers who work with AI prompts. Save reusable prompts as plain Markdown, check templates for common placeholder mistakes, and render a prompt with supplied values — without an API key or external service.

PromptLab is intentionally provider-neutral: it helps with the prompt workflow, not with calling a particular model.

## Requirements

- Python 3.10 or newer
- No third-party packages

## Quick start

```bash
python promptlab.py list
python promptlab.py check examples/code-review.md
python promptlab.py render examples/code-review.md --var language=Python --var diff="def add(a, b): return a + b"

# Save the rendered prompt to a file (will not overwrite an existing file)
python promptlab.py render examples/code-review.md --var language=Python --var diff="def add(a, b): return a + b" --output rendered-review.md

# Use --force only when you intentionally want to replace an existing output file
python promptlab.py render examples/code-review.md --var language=Python --var diff="def add(a, b): return a + b" --output rendered-review.md --force
```

## Commands

- `list [directory]` lists Markdown prompt files (defaults to the bundled examples).
- `check FILE` reports placeholders and basic template issues.
- `render FILE --var name=value` substitutes provided values and prints the result.
- `render FILE --var name=value --output PATH` saves the rendered prompt to a file; existing files are protected unless you explicitly pass `--force`.
- `init PATH` creates a starter prompt file without overwriting an existing file.

See `python promptlab.py --help` for details.

## Tests

```bash
python -m unittest discover -s . -p 'test_*.py' -v
```

## Why local-first?

- No model provider is required.
- No network requests are made.
- Prompt content stays in your local files and terminal.
- Templates can be reviewed and version-controlled like ordinary source code.

## Scope and limitations

PromptLab performs simple text-template substitution, not model inference. It does not execute prompt content. Placeholder names must use letters, digits, or underscores and begin with a letter or underscore. Values are plain text; this tool does not attempt to escape content for a particular model or downstream format.

## Contributing

Bug reports, examples, small improvements, and tests are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md). Please use fictional/sample inputs and do not post API keys, passwords, access tokens, customer data, or confidential prompts in issues or commits.

## License

MIT. See [LICENSE](LICENSE).
