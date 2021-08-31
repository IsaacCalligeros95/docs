---
title: Assigning a team to a tenant
description: This part of the guide demonstrates scoping an Octopus Team to a Tenant
position: 30
hideInThisSectionHeader: true
---

The Octo Pet Shop application has two development teams (Avengers and Radical) that are concurrently developing features for the application.  Scoping the team to their specific tenant will ensure they can only deploy to their dedicated infrastructure.

## Scoping a team to a tenant

Once you've created your team, click on the **USER ROLES** tab.

![](images/octopus-teams-avenger.png "width=500")

Click on **INCLUDE USER ROLE** then select the role to include for the team.  After the role has been selected, click on **DEFINE SCOPE**

![](images/octopus-teams-roles.png "width=500")

Select the tenant and click **APPLY**

![](images/octopus-teams-role-tenant.png "width=500")

This configures the team with `Release Creator` and `Project Deployer` permissions to any project with the Tenant `OctoPetShop-Team-Avengers`

![](images/octopus-teams-userroles.png "width=500")

<span><a class="btn btn-secondary" href="/docs/tenants/guides/multi-tenant-teams/creating-new-tenants">Previous</a></span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span><a class="btn btn-success" href="/docs/tenants/guides/multi-tenant-teams/deploying-team-tenant">Next</a></span>