# cfn-security

Continuous Security tool suite for CloudFormation templates using GitHub Actions.

`cfn-security` docker image is docker image containing static code analysis tools for security AWS CloudFormation templates. The docker image is **designed to run without requiring any AWS credentials** making it easy to add to your GitHub Actions or Gitlab-CI. To use this tool in GitHub Actions please see [cfn-security](https://github.com/marketplace/actions/cfn-security)

## Security Tools

The following summarizes the CloudFormation security analysis tools leveraged in cfn-security.

1. cfn-lint
2. cfn-nag
3. checkov

### cfn-lint (cfn-python-lint)

[cfn-lint](https://github.com/aws-cloudformation/cfn-python-lint) by AWS. Validate AWS CloudFormation yaml/json templates against the AWS CloudFormation Resource Specification and additional checks. Includes checking valid values for resource properties and best practices.

Utilization:

```sh
## scan an entire directory
CLOUDFORMATION_DIRECTORY="./cloudformation/"
cfn-lint $CLOUDFORMATION_DIRECTORY
```

### cfn-nag

[cfn-nag](https://github.com/stelligent/cfn_nag) by Stelligent, looks for patterns in CloudFormation templates that may indicate insecure infrastructure.

Utilization:

```sh
## scan an entire directory
CLOUDFORMATION_DIRECTORY="./cloudformation/"
cfn_nag_scan --input-path $CLOUDFORMATION_DIRECTORY
```

### checkov.io

[checkov](https://github.com/bridgecrewio/checkov) is an open source static code analysis tool for infrastructure-as-code. It scans cloud infrastructure managed in `Cloudformation`, Terraform, Kubernetes, Arm templates or Serverless Framework and detects misconfigurations.

Utilization:

```sh
## scan an entire directory
CLOUDFORMATION_DIRECTORY="./cloudformation/"
checkov -d $CLOUDFORMATION_DIRECTORY
```
