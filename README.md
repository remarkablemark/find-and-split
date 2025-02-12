# split-files

[![version](https://badgen.net/github/release/remarkablemark/split-files)](https://github.com/remarkablemark/split-files/releases)
[![test](https://github.com/remarkablemark/split-files/actions/workflows/test.yml/badge.svg)](https://github.com/remarkablemark/split-files/actions/workflows/test.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

✂️ Split files with GitHub Actions.

## Quick Start

```yaml
on: push
jobs:
  split-files:
    runs-on: ubuntu-latest
    steps:
      - name: Split Files
        uses: remarkablemark/split-files@v1
```

## Usage

See [action.yml](action.yml)

**Basic:**

```yaml
- uses: remarkablemark/split-files@v1
```

## Inputs

### `version`

**Optional**: The version. Defaults to `1.2.3`:

```yaml
- uses: remarkablemark/split-files@v1
  with:
    version: 1.2.3
```

## Contributions

Contributions are welcome! 👋

## License

[MIT](LICENSE)
