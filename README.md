# cfn-security

Continuous Security tool suite for CloudFormation templates using GitHub Actions.

`cfn-security` docker image is docker image containing static code analysis tools for security AWS CloudFormation templates. The docker image is **designed to run without requiring any AWS credentials** making it easy to add to your GitHub Actions or Gitlab-CI.

## Security Tools

The following summarizes the CloudFormation security analysis tools leveraged in cfn-security.

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

### cfn-guard

[cfn-guard](https://github.com/aws-cloudformation/cloudformation-guard/tree/master/cfn-guard) is a command line tool for validating AWS CloudFormation resources against policy.

Utilization:

```sh
## scan an entire directory
CLOUDFORMATION_DIRECTORY="./cloudformation/"
tree -fai $CLOUDFORMATION_DIRECTORY | grep -e ".yml$" -e ".yaml$" -e ".json$" | cfn-guard check
```
