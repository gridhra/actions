# yiegle/check-draft-code-remains

## How to use

You need to call ``actions/checkout`` before use this action.

Here are some examples.

ex1: check ``console.log()`` remains in your frontend source codes.

```yaml
- uses: actions/checkout@v4
- uses: yiegle/actions/check-draft-code-remains@main
    with:
        draft-code: 'console.log'
        path-to-check: './frontend/src'
```

ex2: check ``FIXME:`` remains in your repo.
```yaml
- uses: actions/checkout@v4
- uses: yiegle/actions/check-draft-code-remains@main
    with:
        draft-code: 'FIXME:'
```

## Usecase

Write workflow as bellow, If you want to operate to eliminate all FIXME: before the code enters the main branch.

```yaml
name: 'check fixme remains'

on:
  pull_request:
    branches:
      - 'main'

jobs:
    check-fixme:
        runs-on: ubuntu-latest
        steps:
            - uses: actions/checkout@v4
            - uses: yiegle/actions/check-draft-code-remains@main
                with:
                    draft-code: 'FIXME:'
```
