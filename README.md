# run-deployment-step

GitHub action to run a Bash deployment command, upload a status badge gist with
the result, and optionally print a comment about the command.

## Usage

See [action.yml](action.yml).

## Example Workflow

```yaml
name: Deploy

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install dependencies
        uses: colinparsonsme/run-deployment-step@v1
        with:
          auth: ${{ secrets.GITHUB_GIST_TOKEN }}
          command: npm ci --production
          gist-id: ${{ secrets.INSTALL_DEPENDENCIES_BADGE_GIST_ID }}
          badge-label: Dependencies install
          comment:
            "We use `npm ci` instead of `npm i` because this step is running in
            a CI environment, and we don't want to update the package.json."

      # more deployment steps here...
```

## License

See the [License](LICENSE).

## Contributing

See the [Contributing Guidelines](CONTRIBUTING.md).

### Contributor Code of Conduct

See the [Code of Conduct](CODE-OF-CONDUCT.md).

## Contact

If you're interested in getting in touch outside of this project, check out
[colinparsons.com](https://colinparsons.com).
