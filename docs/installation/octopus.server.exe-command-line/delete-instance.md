---
title: Delete instances
description:  Deletes an instance of the Octopus service
position: 41
---

Use the Delete Instance command to delete an instance of the Octopus service.

**Delete Instance options**

```text
Usage: octopus.server delete-instance [<options>]

Where [<options>] is any of:

      --instance=VALUE       Name of the instance to use

Or one of the common options:

      --help                 Show detailed help for this command
```

## Basic example

This example deletes the Octopus Server instance on the machine named `MyNewInstance`:

```text
octopus.server delete-instance --instance="MyNewInstance"
```
