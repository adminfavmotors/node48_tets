# Deployments

## Test Repository Mode

This repository is a test mirror of the active project, so the deploy workflow is intentionally simpler than the production repo.

Current behavior:

- push to `main` triggers deploy
- manual deploy by explicit ref is still available
- no GitHub Actions environment gate is required
- no immutable deployment tag is created

## Why The Workflow Was Simplified

The production repo can justify extra controls like:

- environment approval gates
- protected production metadata
- immutable deploy tags

The test repo is meant for fast iteration, so those controls were removed here to reduce friction during deploy runs.

## Transport Contract

Deploys use `rsync` over `SSH`, not plain `FTP`.

Before the workflow can deploy successfully:

1. Enable `SSH` access for the SEOHOST hosting account.
2. Add the GitHub Actions public key to SEOHOST in `Funkcje zaawansowane -> Klucze SSH` and authorize it.
3. Store the matching private key in a GitHub Actions secret named `SEOHOST_GITHUB_ACTIONS_RSA`.
   The workflow accepts either the raw private key or a base64-encoded version of the same key.

The current workflow still deploys with these values:

- host: `h79.seohost.pl`
- user: `srv110507`
- port: `57185`
- target path: `domains/node48.pl/public_html/`

## Important Warning

This test repository currently still points to the same SEOHOST destination as the mirrored project.

That means:

- deploy friction is lower here
- but the deploy target is not isolated by this repository alone

If this repository should deploy to a separate test site, update the host, user, port, target path, and GitHub secret setup before using deploy workflows.

## GitHub Settings Note

If pushes or merges are still blocked after these file changes, that blocker is not in the repository files. It will usually be in GitHub settings such as:

- branch protection
- rulesets
- repository environment settings
