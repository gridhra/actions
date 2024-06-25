# yiegle/actions/ecs-service-toggle

## Overview

This GitHub Action allows you to start, stop, or toggle the state of an ECS service based on user input. The action performs the following steps:

Determine New Desired Count: Based on the input action (start, stop, or toggle), the action determines the new desired count for the ECS service. If start is specified, the desired count is set to 1. If stop is specified, the desired count is set to 0. If toggle is specified, the current desired count is fetched from the ECS service, and it is toggled between 0 and 1.

Update ECS Service Desired Count: The action updates the ECS service with the new desired count. The action does not wait for the service to stabilize after the update.


## Inputs

action: (Required) The action to perform on the ECS service. Valid values are start, stop, and toggle. Default is toggle.

cluster: (Required) The ARN of the ECS cluster.

service: (Required) The ARN of the ECS service.

region: (Required) The AWS region where your ECS cluster is located.


## Example Usage

```yaml
name: toggle ecs exec

on:
  workflow_dispatch:

jobs:
  toggle-ecs-exec:
    runs-on: ubuntu-latest

    steps:
    - name: checkout code
      uses: actions/checkout@v4

    - name: configure aws credentials
      uses: aws-actions/configure-aws-credentials@v2
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: ap-northeast-1

    - name: toggle ecs service
      uses: ./path/to/your/composite/action
      with:
        action: toggle
        cluster: arn:aws:ecs:ap-northeast-1:your-account-id:cluster/sample-cluster
        service: arn:aws:ecs:ap-northeast-1:your-account-id:service/sample-cluster/sample-service
        region: ap-northeast-1
```


## Note

Ensure that your AWS credentials are configured properly using the aws-actions/configure-aws-credentials action before using this action to manage your ECS services.

This action will not wait for the ECS service to stabilize after updating the desired count.
