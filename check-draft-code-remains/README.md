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
