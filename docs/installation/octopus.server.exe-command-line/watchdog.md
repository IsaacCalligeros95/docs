---
title: Watchdog
description:  Configure a scheduled task to monitor the Octopus service(s).
position: 230
---

Use the watchdog command to configure a scheduled task to monitor the Octopus service(s).

**Watchdog options**

```text
Usage: octopus.server watchdog [<options>]

Where [<options>] is any of:

      --create               Create the watchdog task for the given instances
      --delete               Delete the watchdog task for the given instances
      --interval=VALUE       The interval, in minutes, at which that the
                               service(s) should be checked (default: 5)
      --instances=VALUE      List of instances to be checked (default: *)

Or one of the common options:

      --help                 Show detailed help for this command
```

## Basic examples

This example creates a watchdog task for the `default` instance:

```text
octopus.server watchdog --create --instances="default"
```

This example deletes the watchdog tasks for instances named `default` and `MyNewInstance`:

```text Comma separated
octopus.server watchdog --delete --instances="default,MyNewInstance"
```
```text Semi-colon separated
octopus.server watchdog --delete --instances="default;MyNewInstance"
```
