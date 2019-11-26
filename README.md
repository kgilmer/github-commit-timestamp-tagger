# Github Commit Timestamp Tagger

This action met a very simple need I had that nothing else seemed to do: it generates
a tag for commits on a branch where the tagname is composed of a base version and
a timestamp.

Nothing fancy. Just a way to tag commits to, for example, a development branch so
a build can be produced for each merge.

## Usage

Add a workflow file like the following to your project:

```
name: "Tag commits on develop"

on:
  push:
    branches:
      - develop

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Apply a tag to the new commit
      uses: mcpierce/github-commit-timestamp-tagger@master
      with:
        repo-token: "${{ secrets.GITHUB_TOKEN }}"
        base_version: "v0.5.0"
```