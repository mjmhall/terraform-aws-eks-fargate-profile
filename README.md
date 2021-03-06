# terraform-aws-eks-fargate-profile

Terraform module to provision an EKS Node Group for [Elastic Container Service for Kubernetes](https://aws.amazon.com/eks/).

Instantiate it multiple times to create many EKS node groups with specific settings such as GPUs, EC2 instance types, or autoscale parameters.

Based on [Terraform Resource](https://www.terraform.io/docs/providers/aws/r/eks_fargate_profile.html)

## Usage example

Here's the gist of using it directly from github.

```hcl

    module "eks_fargate" {
      source               = "git::https://github.com/terraform-module/terraform-aws-eks-fargate-profile.git?ref=master"
      tags                 = var.tags
      subnet_ids           = var.subnet_ids
      cluster_name         = var.cluster_name
      kubernetes_namespace = var.namespace
      kubernetes_labels    = var.labels
    }
```

## Assumptions

## Available features

## Module Variables

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| cluster\_name | Cluster name | string | n/a | yes |
| enabled | Whether to create the resources. Set to `false` to prevent the module from creating any resources | bool | `"true"` | no |
| labels | Key-value mapping of Kubernetes labels for selection | map(string) | `{}` | no |
| namespace | Kubernetes namespace for selection | string | n/a | yes |
| subnet\_ids | Identifiers of private EC2 Subnets to associate with the EKS Fargate Profile. These subnets must have the following resource tag: kubernetes.io/cluster/CLUSTER_NAME (where CLUSTER_NAME is replaced with the name of the EKS Cluster) | list(string) | n/a | yes |
| tags | Additional tags (e.g. `{ Deployed = "xxxx" }` | map(string) | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| eks\_fargate\_profile\_arn | Amazon Resource Name (ARN) of the EKS Fargate Profile |
| eks\_fargate\_profile\_id | EKS Cluster name and EKS Fargate Profile name separated by a colon |
| eks\_fargate\_profile\_role\_arn | ARN of the EKS Fargate Profile IAM role |
| eks\_fargate\_profile\_role\_name | Name of the EKS Fargate Profile IAM role |
| eks\_fargate\_profile\_status | Status of the EKS Fargate Profile |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Commands

<!-- START makefile-doc -->
```
$ make help 
hooks                          Commit hooks setup
validate                       Validate with pre-commit hooks
changelog                      Update changelog
release                        Create release version 
```
<!-- END makefile-doc -->


## License

Copyright 2019 ivankatliarhcuk

MIT Licensed. See [LICENSE](./LICENSE) for full details.

## How to Contribute

Submit a pull request

# Authors

Currently maintained by [Ivan Katliarchuk](https://github.com/ivankatliarchuk) and these [awesome contributors](https://github.com/terraform-module/terraform-module-blueprint/graphs/contributors).
