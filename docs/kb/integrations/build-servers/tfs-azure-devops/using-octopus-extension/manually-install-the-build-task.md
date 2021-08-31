---
title: Manually install the build task (Not Recommended)
description: This guide covers how to manually install the Octopus Release build task into Microsoft Azure DevOps/TFS.
---

If you'd like more control over the build task we've created, you can manually upload it yourself using Microsoft's [TFX CLI tool](https://github.com/Microsoft/tfs-cli).

This is also the method you'll need to use if you want to install the build task in your on-premises Azure DevOps/TFS instance.

## Installing the build task {#ManuallyinstalltheBuildTask(notrecommended)-InstallingtheBuildTask}

Clone the repository locally

```powershell
git clone https://github.com/OctopusDeploy/OctoTFS.git
```

![](images/3278346.png "width=500")

Install TFX-CLI using npm. You'll obviously need node installed to do this.

```powershell
npm install -g tfx-cli
```

![](images/3278347.png "width=500")

:::warning
If you are using an on-premises TFS instance, authentication can only be performed using Basic authentication. [See this page](https://github.com/Microsoft/tfs-cli/blob/master/docs/configureBasicAuth.md) for information on how to enable it for your on-premises server.

When you log in, use `--authType basic` to authenticate that way. NTLM authentication is coming to the TFX tool soon.
:::

Create a new **Personal Access Token** (PAT) in Azure DevOps/TFS in the **Security** tab for your Profile.

![](images/3278348.png "width=500")

![](images/3278349.png "width=500")

Specify All scopes. You can revoke this token as soon as the task is uploaded.

![](images/3278350.png "width=500")

Login to your Visual Studio or Azure DevOps/TFS account using the TFX-CLI tool

```powershell
 tfx login
```

![](images/3278375.png "width=500")
Navigate to the cloned folder which is the root of the extension at which point you can install dependencies and build the extension and all associated tasks

```
npm install
npm run build
```

Use the TFX-CLI tool to upload the Octopus Create Release task. You will need to point at the `dist\tasks\CreateOctopusRelease` folder in the cloned repository.

```powershell
 tfx build tasks upload <path-to-task>
```

![](images/3278376.png "width=500")
