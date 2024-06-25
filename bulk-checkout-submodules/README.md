## yiegle/actions/bulk-checkout-submodules

## Overview

This GitHub Action allows you to bulk checkout multiple submodules in your repository. Before using this action, ensure that you have already used actions/checkout to checkout your main repository. Note that this action only works for submodules hosted in public repositories.


## Inputs

submodule-paths: (Required) A comma-separated list of submodule paths (e.g., submodules/module1,submodules/module2).


## Usage Example

```yaml
name: Bulk Checkout Submodules

on: [push]

jobs:
  checkout-submodules:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Bulk Checkout Submodules
      uses: ./path/to/your/composite/action
      with:
        submodule-paths: 'submodules/module1,submodules/module2'
```


## Note

Ensure that you have already checked out your main repository using actions/checkout before invoking this action.

This action only works for submodules hosted in public repositories.
