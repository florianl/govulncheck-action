# govulncheck-action

This action runs [govulncheck](https://go.dev/blog/vuln) to identify vulnerabilities in your Go code.


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
    - uses: actions/checkout@v2
      with:
        fetch-depth: 1
    - uses: florianl/govulncheck-action@latest
```

## Options

### `install-go`
Let the action install a version of Go. If set to false, the action expects you to have installed Go already. By default Go 1.19 will be installed.

### `working-directory`
Path to the working directory govulncheck should be executed in.

### `vulncheck-version`
Specify a verion of govulncheck to install. By default latest will be used.