# find-and-split

[![version](https://badgen.net/github/release/remarkablemark/find-and-split)](https://github.com/remarkablemark/find-and-split/releases)
[![test](https://github.com/remarkablemark/find-and-split/actions/workflows/test.yml/badge.svg)](https://github.com/remarkablemark/find-and-split/actions/workflows/test.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

✂️ Find and split files with GitHub Actions.

## Quick Start

Find and split files using the [matrix strategy](https://docs.github.com/actions/writing-workflows/choosing-what-your-workflow-does/running-variations-of-jobs-in-a-workflow):

```yaml
on: push
jobs:
  find-and-split:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        chunk: [1/2, 2/2]
    steps:
      - name: Find and split files
        uses: remarkablemark/find-and-split@v1
        id: my-files
        with:
          pattern: '*.txt'
          chunk: ${{ matrix.chunk }}
      - name: Print files
        run: echo ${{ steps.my-files.outputs.files }}
```

## Usage

See [action.yml](action.yml)

**Basic:**

```yaml
- uses: remarkablemark/find-and-split@v1
  with:
    pattern: '*.txt'
    chunk: 1/3
```

## Inputs

### `chunk`

**Required**: The chunk as a fraction (e.g., 1/2). The numerator is the chunk index and the denominator is the chunk total.

```yaml
- uses: remarkablemark/find-and-split@v1
  with:
    chunk: 1/2
```

> [!NOTE]
> The chunk limit is 256 because that's the maximum jobs per workflow run.

### `pattern`

**Required**: The filename pattern.

```yaml
- uses: remarkablemark/find-and-split@v1
  with:
    pattern: '*.txt'
```

> Special shell pattern matching characters (`[`, `]`, `*`, and `?`) may be used as part of the pattern.
> These characters may be matched explicitly by escaping them with a backslash (`\`).

### `directory`

**Optional**: The directory. Defaults to the current working directory.

```yaml
- uses: remarkablemark/find-and-split@v1
  with:
    directory: .
```

### `delimiter`

**Optional**: The delimiter. Defaults to a single space.

```yaml
- uses: remarkablemark/find-and-split@v1
  with:
    delimiter: ' '
```

## Outputs

### `files`

The list of files.

## License

[MIT](LICENSE)
