# conda-forge infrastructure

This repository holds common configurations and settings for key pieces of the
conda-forge infrastructure.

> [!NOTE]
> This is not a forum for end-user questions

## Sync-secrets

The `sync-secrets` pulumi project syncs secrets from the conda-forge 1password vault to relevant services (eg. to GitHub).

### Running locally

* Install the 1password cli
* Export environment variables:
  * `GITHUB_TOKEN` (permissions to `repo` and `admin:org`)
  * `OP_SERVICE_ACCOUNT_TOKEN` (token for 1password service account)
*  Setup pulumi (only needs to be run once)
```
$ pulumi install
$ pulumi plugin install resource onepassword --server github://api.github.com/1Password/pulumi-onepassword
```
* Apply changes
```
$ pulumi up
```

### Try it out with GHA

[`.github/workflows/push-1password-secrets-to-gha`](https://github.com/conda-forge/infrastructure/blob/main/.github/workflows/push-1password-secrets-to-gha.yaml)

Try it out by:
* create and push a branch names with following the pattern "push-secrets-*"
* observe the run in github action that populates secrets
