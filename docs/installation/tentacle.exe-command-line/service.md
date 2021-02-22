---
title: Service
description: Using the Tentacle.exe command line executable to start, stop, install and configure the Tentacle service.
---

Start, stop, install and configure the Tentacle service.

**Service options**

```text
Usage: tentacle service [<options>]

Where [<options>] is any of:

      --start                Start the Windows Service if it is not already
                               running
      --stop                 Stop the Windows Service if it is running
      --restart              Restart the Windows Service if it is running
      --reconfigure          Reconfigure the Windows Service
      --install              Install the Windows Service
      --username, --user=VALUE
                             Username to run the service under
                               (DOMAIN\Username format). Only used when --
                               install or --reconfigure are used.  Can also be
                               passed via an environment variable
                               OCTOPUS_SERVICE_USERNAME.
      --uninstall            Uninstall the Windows Service
      --password=VALUE       Password for the username specified with --
                               username. Only used when --install or --
                               reconfigure are used. Can also be passed via an
                               environment variable OCTOPUS_SERVICE_PASSWORD.
      --dependOn=VALUE
      --instance=VALUE       Name of the instance to use, or * to use all
                               instances

Or one of the common options:

      --help                 Show detailed help for this command
```

## Basic examples

This example stops the default Tentacle service:

```text
tentacle service --stop
```

This example restarts the Tentacle service for instance `MyNewInstance`:

```text
tentacle service --restart --instance="MyNewInstance"
```

This example uninstalls the Tentacle service for instance `MyNewInstance`:

```text
tentacle service --uninstall --instance="MyNewInstance"
```
