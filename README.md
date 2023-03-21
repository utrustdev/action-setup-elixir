# Github Action - Setup Elixir

Configures Elixir, fetches dependencies, and manages build caching.

## Usage
Add the following step and matrix to your Action.

```yaml
jobs:
  setup:
    strategy:
      matrix:
        elixir: ['1.13']
        otp: ['24.3.4']

    steps:
      - name: Setup Elixir Project
        uses: ./.github/actions/elixir_setup
        with:
          elixir-version: ${{ matrix.elixir }}
          otp-version: ${{ matrix.otp }}
          build-flags: --all-warnings --warnings-as-errors
          hex-org-key: ${{ secrets.HEX_ORG_KEY }}
```

This action does not:
* Check out the code
* Setup any additional services like Databases or Localstack.

Those need to be setup in each flow.
