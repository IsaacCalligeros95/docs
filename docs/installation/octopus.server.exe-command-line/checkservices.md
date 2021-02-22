---
title: Check services
description:  Checks the Octopus instances are running
position: 30
---

The `checkservices` command checks the Octopus Server instances to see if they are running and start them if they're not.  The [watchdog](/docs/administration/managing-infrastructure/service-watchdog.md) command sets up a scheduled task that calls `checkservices`.

**Check Services options**

```text
Usage: octopus.server checkservices [<options>]

Where [<options>] is any of:

      --instances=VALUE      Comma-separated list of instances to check, or *
                               to check all instances

Or one of the common options:

      --help                 Show detailed help for this command
```

## Basic example

This example checks to see if all of the instances are running on the machine and start them if they are not:

```text
octopus.server checkservices --instances=*
```
