# Publish GOAR 1.1.0 to PyPI

Package name: `goar`
CLI entrypoint: `goar`
License: Apache-2.0

Built artifacts (twine-checked):

```
dist/goar-1.1.0-py3-none-any.whl
dist/goar-1.1.0.tar.gz
```

The name `goar` is currently free on PyPI and TestPyPI.

## One-shot upload (API token)

1. Create a PyPI account: https://pypi.org/account/register/
2. Enable 2FA, then create an API token: https://pypi.org/manage/account/token/
   - Scope: entire account (first upload of a new project) or later restrict to `goar`
3. Upload:

```bash
python3 -m pip install -U twine
export TWINE_USERNAME=__token__
export TWINE_PASSWORD=pypi-AgEIcHlwaS5vcmc...   # paste your token
python3 -m twine upload dist/goar-1.1.0*
```

Dry-run against TestPyPI first (recommended):

```bash
python3 -m twine upload --repository testpypi dist/goar-1.1.0*
pip install -i https://test.pypi.org/simple/ --extra-index-url https://pypi.org/simple goar
```

After the live upload:

```bash
pip install goar
goar --version
```

## Trusted publishing from GitHub (no long-lived token)

This repo includes `.github/workflows/publish.yml`.

1. On PyPI: Publishing → pending publishers
   - Owner: `goarxyz`
   - Repository: `goar-cli`
   - Workflow: `publish.yml`
   - Environment: `pypi`
2. On GitHub: Settings → Environments → create `pypi`
3. Tag a release:

```bash
git tag v1.1.0
git push origin v1.1.0
# then create a GitHub Release from that tag
```

The workflow builds the sdist/wheel and publishes with OIDC. No token is stored in the repo.

## Notes

- First upload claims the name permanently. Do it from the account that should own `goar`.
- This 1.1.0 tree is the local-first package (no telemetry modules). Do not reuse the older `goarxyz/goar` 2.24.2 release workflow that injects a Sentry DSN.
- Making `goarxyz/goar` public is optional for discoverability; PyPI install works regardless.
