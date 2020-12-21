# truncate-sha-action
Truncate commit SHA to the specified field width

## Pre-requisites
Create a workflow .yml file in your repo of .github/workflows directory. An example workflow is available below.

## Inputs:
- `sha` : SHA of commit, default is the current commit SHA triggered the event.
- `field-width` : Specified field width of truncation, default is `7`

## Outputs:
- `sha-origin` : The original SHA.
- `sha-width` ： Truncated field width.
- `sha-short` : Truncated short SHA

## Example workflow
On every push to your repro `test` branch.

```yaml
name: --env-test--

on:
  push:
    branches: test
env:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

jobs:
  test-sha-truncator:
    name: Test truncate SHA to short form
    runs-on: ubuntu-16.04
    steps:
    - name: Use truncate-sha Action
        id: truncate-sha
        uses: tangm421/truncate-sha-action@v1.0
        #with:
        #  sha: ${{github.sha}}
        #  field-width: 7
    - name: Show Test
        if: success()
        shell: bash
        run: |
          echo sha-origin: ${{ steps.truncate-sha.outputs.sha-origin }}
          echo sha-width: ${{ steps.truncate-sha.outputs.sha-width }}
          echo sha-short: ${{steps.truncate-sha.outputs.sha-short}}
```

## TO BE CONTINUED...

[![Website](https://img.shields.io/website?down_message=offline&label=explore%20my%20blog&logo=Internet%20Explorer&style=for-the-badge&up_message=online&url=https%3A%2F%2Fblog.luanhui.cf "Welcome to my blog")](https://blog.luanhui.cf)