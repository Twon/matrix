# matrix
A matrix implementation for standardisation by wg21

### Installing Pre-commit checks

This repository is set up with [pre-commit]https://pre-commit.com/) to manage git pre-commit hooks.  To install the commit hooks for this repository locally run:
```bash
pre-commit install
```

Or if you prefer to run the checks manually then run:
```bash
pre-commit run --all-files
```

In case you forget to install or run these it will be run as part of the CI so any failured will be raised once you submit a pull request.
