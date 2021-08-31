---
title: Terraform
description: Octopus Deploy can help you automate provisioning infrastructure with Terraform using runbooks.
position: 70
---

Terraform is a popular, platform agnostic implementation of Infrastructure as Code (IaC).  Terraform is designed to ensure that the resources it creates are kept within the desired state, this is known as Desired State Configuration (DSC).

Out of the box, Octopus Deploy comes with built-in step templates for using Terraform:
- Apply a Terraform template
- Destroy Terraform resources
- Plan to apply a Terraform template
- Plan a Terraform destroy

With runbooks, you can use Terraform to create your infrastructure resources.