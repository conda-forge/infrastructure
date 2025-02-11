# conda-forge infrastructure

This repository holds common configurations and settings for key pieces of the
conda-forge infrastructure.

> [!NOTE]
> This is not a forum for end-user questions

## Sync-secrets-azure

The `sync-secrets-azure` pulumi project syncs secrets from the conda-forge 1password vault to Azure

### Running locally

* Install the 1password cli
* Export environment variables:
  * `AZDO_PERSONAL_ACCESS_TOKEN` (api token for AZURE)
  * `AZDO_ORG_SERVICE_URL` (org service url for AZURE)
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

[`.github/workflows/push-1password-secrets-to-azure`](https://github.com/conda-forge/infrastructure/blob/main/.github/workflows/push-1password-secrets-to-azure.yaml)

Try it out by:
* create and push a branch name following the pattern "azure-push-secrets-*" OR [manually run](https://docs.github.com/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/manually-running-a-workflow) the [1Password-to-Azure workflow](https://github.com/conda-forge/infrastructure/actions/workflows/push-1password-secrets-to-azure.yaml)
* observe the run in github action that populates secrets

## Sync-secrets-gha

The `sync-secrets-gha` pulumi project syncs secrets from the conda-forge 1password vault to Github

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
* create and push a branch names with following the pattern "push-secrets-*" OR [manually run the workflow](https://docs.github.com/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/manually-running-a-workflow)
* observe the run in github action that populates secrets

## Sync-secrets-heroku

The `sync-secrets-heroku` pulumi project syncs secrets from the conda-forge 1password vault to Heroku

### Running locally

* Install the 1password cli
* Export environment variables:
  * `HEROKU_API_KEY` (api token for heroku)
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

[`.github/workflows/push-1password-secrets-to-heroku`](https://github.com/conda-forge/infrastructure/blob/main/.github/workflows/push-1password-secrets-to-heroku.yaml)

Try it out by:
* create and push a branch named with the pattern "heroku-push-secrets-*" OR [manually run](https://docs.github.com/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/manually-running-a-workflow) the [1Password-to-Heroku workflow](https://github.com/conda-forge/infrastructure/actions/workflows/push-1password-secrets-to-heroku.yaml)
* observe the run in github action that populates secrets

### Sponsored by Pulumi

<img src="https://www.pulumi.com/images/pricing/team-oss.svg" width=400 />
