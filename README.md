# Submodule Checkout Action

This action checks out a private or public submodule hosted within GitHub.

## Usage

````
- uses: actions/checkout@v3
- uses: kilianweisl/submodule-checkout@1.0.0
````

## Private Repositories

If you want to check out private repositories, provide an additional (private) SSH-Key:
````
- uses: actions/checkout@v3
- uses: kilianweisl/submodule-checkout@1.0.0
  with:
    ssh-key: '${{ secrets.SSH_PRIVATE_KEY }}'
````

Make sure, that `SSH_PRIVATE_KEY` is added as secret variable in the parent repository and the corresponding public key as "deploy key" in the submodule repository (Settings->Deploy keys).

## ChangeLog

The original code has been updated in order to make it work:
- New GitHub RSA signature
- `git config --global --add safe.directory /github/workspace` in `entrypoint.sh` (before `git submodule update --init --recursive` is executed).

## License
MIT

## Original Author
James Webb