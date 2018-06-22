# Integrations operations

This folder contains useful scripts and commands to update integrations in bulk.

## Env vars
- `GITHUB_TOKEN`: To query/update GitHub.
- `GITHUB_USER`: For commits. Optional, if not present it will use the system configuration.
- `GITHUB_EMAIL`: For commits. Optional, if not present it will use the system configuration.

## list-integrationss

Lists all the integrations.
Options:
- `--verbose`
- `--repositories`: If present, it will return the integrations repositories (they are getting deprecated)
- `--searchMods=<string>`: GitHub search mods to query the repositories (`is:private`, `is:public`).
- `--monorepoPath=<string>`: Local path where the monorepo lives. Default to `..`.

## list-updated-integrations

Lists all the updated integrations since the specified commit or `refs/heads/master`.
Options:
- `--verbose`
- `--monorepoPath=<string>`: Local path where the monorepo lives. Default to `..`.
- `--commit=<string>`: Commit or reference to compare with the current workspace. Default to `refs/heads/master`.

## migrate-integration

Migrates the integration repo into the monorepo:
1. Copies the integration code in the monorepo.
1. Updates references in package.json for the integration.
1. Commits the integration code.
1. Updates the integration repo with a notice.
1. Comments in all opened issues and pull requests and copies them to the monorepo as issues.
1. Marks the repo as `migrated`.

Options:
- `--verbose`
- `--integration=<name>`
- `--monorepoPath=<string>`: Local path where the monorepo lives. Default to `..`.
- `--tmpPath=<string>`: Temporal folder. Default to `/tmp/integrations`.