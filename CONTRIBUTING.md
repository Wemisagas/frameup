# Contributing

Thanks for taking the time to contribute! Here's how to get started.

## Reporting bugs

Open an issue using the bug report template. Include as much detail as possible — OS, Node version, the URL you were trying to capture, and the full error output.

## Suggesting features

Open an issue using the feature request template. Explain the use case — what were you trying to do and why the current tool didn't cover it.

## Submitting a pull request

1. Fork the repo and create a branch from `main`
2. Make your changes
3. Test locally with a few different URLs to make sure nothing is broken
4. Open a pull request with a clear description of what you changed and why

## Development setup

```bash
git clone https://github.com/zjebinsky/frameup.git
cd frameup
bun install
bunx playwright install chromium
```

Then run it against any URL:

```bash
bun run frameup.ts https://example.com images
bun run frameup.ts https://example.com video
```

## Guidelines

- Keep changes focused — one thing per PR
- Don't add dependencies unless absolutely necessary
- Match the existing code style
