# Automate Haskell releases

Based on a git tag:

- Bump cabal file version
- Upload to Hackage

## Example

You need to make sure to [generate a Hackage token](http://hackage.haskell.org/users/account-management) 
and save it as a secret under the name `HACKAGE_AUTH_TOKEN`.

```yaml
name: "Release"
on:
  push:
    tags:
      - v**
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: cachix/haskell-release-action@v1
        with:
          - hackage-token: "${{ secrets.HACKAGE_AUTH_TOKEN }}"
```