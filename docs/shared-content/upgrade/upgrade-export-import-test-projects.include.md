### Export subset of projects

All versions of Octopus Deploy since version 3.x has included a [data migration tool](/docs/administration/data/data-migration.md).  The Octopus Manager only allows for the migration of all the data.  We only need a subset of data.  Use the [partial export](/docs/administration/octopus.migrator.exe-command-line/partial-export.md) command-line option to export a subset of projects. 

Run this command for each project you wish to export on the main, or production, instance.  Create a new folder per project:

```
Octopus.Migrator.exe partial-export --instance=OctopusServer --project=AcmeWebStore --password=5uper5ecret --directory=C:\Temp\AcmeWebStore --ignore-history --ignore-deployments --ignore-machines
```

:::hint
This command ignores all deployment targets to prevent your test instance and your main instance from deploying to the same targets.
:::

### Import subset of projects

The data migration tool also includes [import functionality](/docs/administration/octopus.migrator.exe-command-line/import.md).  First, copy all the project folders from the main instance to the test instance.  Then run this command for each project:

```
Octopus.Migrator.exe import --instance=OctopusServer --password=5uper5ecret --directory=C:\Temp\AcmeWebStore
```