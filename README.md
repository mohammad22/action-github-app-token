# action-remote-github-app-token
A fork of [getsentry/action-github-app-token](https://github.com/getsentry/action-github-app-token).

This uses GitHub Apps to fetch a GitHub auth token for a Remote GitHub App installation.
The GitHub App is used to authorize API access across multiple repositories.

## Development

Install the dependencies
```bash
$ yarn
```

Build the typescript and package it for distribution
```bash
$ yarn dist
```

## Usage

You will need to provide the GitHub App ID and private key. The action will then provide a `token` output.

```
  - name: my-app-install token
    id: my-app
    uses: mohammad22/action-github-app-token@v1.0.8
    with:
      remoteGithubApiUrl: https://api.github.com
      app_id: ${{ secrets.APP_ID }}
      private_key: ${{ secrets.APP_PRIVATE_KEY }}

  - name: Checkout private repo
    uses: actions/checkout@v2
    with:
      repository: mohammad22/my-private-repo
      token: ${{ steps.my-app.outputs.token }}
```
