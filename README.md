# code-report
Uploads an artifact containing code quality reports

The aim of this action is to upload an artifact containing code quality reports. The artifact is uploaded to the
workflow run that triggered the action. The artifact is named `code-report` by default and contains one file, named
`code-report.yml` by default.

Currently, the following code quality reports are reported:

- [Coverage.py](https://coverage.readthedocs.io/en/latest/) as a percentage integer, as reported by the `coverage report --format=total`
  command. The coverage percentage is reported as the `python-coverage` key in the report file.

## Usage

This is an example of how to use this action in an existing workflow:

```yaml
jobs:
  - name: Test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
      - run: pip install coverage
      - run: coverage run -m unittest
      - uses: leukeleu/code-report@v1
```

## Inputs

### `artifact-name`

The name of the artifact to upload. Default `"code-report"`.

### `filename`

The name of the report file in the artifact. Default `"code-report.yml"`.


## Artifacts

The action uploads an artifact containing a YAML file with the code quality reports. The artifact is named `code-report`
by default and contains one file, named `code-report.yml` by default.

Example of the `code-report.yml` file:

```yaml
python-coverage: 100
```
