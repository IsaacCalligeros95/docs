---
title: Region specific workers
description: Use workers in specific regions
position: 60
hideInThisSectionHeader: true
---

The SecOps team at Car Rental have implemented the policy that when a deployment occurs, the infrastructure used must reside within the same region datacenter.  Database deployments for Car Rental are handled by [workers](/docs/infrastructure/workers/index.md), so the deployment process needs to automatically select the correct worker during a deployment. 

## Region worker pools

To accommodate the policy, Car Rental has created distinct worker pools for each Azure region and created a worker for each.


## Worker pool variable

Region specific worker pools are only half of the equation, the deployment still needs to be configured to select the correct pool based on the tenant being deployed to.  To solve this issue, we'll utilize a [worker pool variable](/docs/projects/variables/worker-pool-variables.md).  A worker pool variable is a type of variable that you can add to your project.  Just like other variables, these variables can be scoped to tenant tags


## Configure step to use worker pool variable

The Flyway step of the Car Rental deployment process is configured to run on a worker and utilize the `Project.Worker.Pool` variable


Because the tenants for the Car Rental application have been assigned their appropriate Azure Region tag, Octopus Deploy automatically selects the correct worker when performing a deployment to the tenant.  The `De Moines` tenant is assigned the `Central US` Azure Region tag, below is the worker selected during the deployment for `De Moines` and the members of the Azure Cental US worker pool



<span><a class="btn btn-secondary" href="/docs/tenants/guides/multi-tenant-region/deploying-to-release-ring">Previous</a></span>