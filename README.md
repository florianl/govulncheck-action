# govulncheck-action

This is yet another action using [govulncheck](https://go.dev/blog/vuln) to identify vulnerabilities
in your Go code.It checks the code against known vulnerabilities published in
[pkg.go.dev/vuln](https://pkg.go.dev/vuln/).

## Usage

```yaml
name: "Vulnerability scan"

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ '**' ]

jobs:
  ci:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
      with:
        fetch-depth: 1
    - uses: florianl/govulncheck-action@v0.0.3
```

A more advanced example that includes call stacks and provides a JSON output might look like this:
```yaml
name: "Vulnerability scan"

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ '**' ]

jobs:
  ci:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
      with:
        fetch-depth: 1
    - uses: florianl/govulncheck-action@v0.0.3
      with:
        govulncheck-json: true
        govulncheck-verbose: true
```

## Options

### `install-go`
Let the action install a version of Go. If set to false, the action expects you to have installed Go
already. By default Go 1.19 will be installed.

### `working-directory`
Optional path to the working directory govulncheck should be executed in.

### `govulncheck-json`
Provide JSON output instead of standard text.

### `govulncheck-tags`
Comma-seprated list of Go build tags.

### `govulncheck-verbose`
Print a full call stack for each identified vulnerability.

### `govulncheck-version`
Specify a verion of govulncheck to install. By default latest will be used.