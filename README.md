<a href="https://cast.ai">
    <img src="https://cast.ai/wp-content/themes/cast/img/cast-logo-dark-blue.svg" align="right" height="100" />
</a>

Terraform module for creating AWS IAM resources required to connect EKS with CAST AI, providing access through AssumeRole IAM.
==================


Website: https://www.cast.ai

Requirements
------------

- [Terraform](https://www.terraform.io/downloads.html) 0.13+

Using the module
------------

A module to create AWS IAM policies and a role to connect to CAST.AI

Requires `castai/castai` and `hashicorp/aws` providers to be configured.

```hcl
module "castai_eks_role_iam" {
  source = "git::https://github.com/Sensedia/terraform-castai-eks-role-iam.git//?ref=1.0.0"

  # Required
  aws_account_id     = var.aws_account_id
  aws_cluster_region = var.aws_cluster_region
  aws_cluster_name   = var.aws_cluster_name
  aws_cluster_vpc_id = var.aws_vpc_id
  castai_user_arn    = var.castai_user_arn

  # Optional
  create_iam_resources_per_cluster = var.create_iam_resources_per_cluster
  attach_ssm_managed_instance_core = var.attach_ssm_managed_instance_core
  attach_ebs_csi_driver_policy     = var.attach_ebs_csi_driver_policy
  attach_custom_instance_policy    = var.attach_custom_instance_policy
  custom_instance_policy_arn       = var.custom_instance_policy_arn # Used if attach_custom_instance_policy = true
}
```

# Examples

Usage examples are located in [terraform provider repo](https://github.com/castai/terraform-provider-castai/tree/master/examples/eks)
