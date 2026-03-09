# doll.report

## what is `doll.report`?
doll.report is a communal infrastructure project, providing a platform for independent uptime tracking
(and downtime alerts) of infrastructure and services.


## How does it work?
The rough idea is that anyone that's interested can create a merge request,
adding their own dashboard definition file into [dashboards/](dashboards/) folder with a merge request, and once approved,
have a [gatus](https://github.com/TwiN/gatus) instance automatically provisioned.

The gatus instance is individual per dashboard and all options are supported.

Upon pushing to the repo [`ansible-lint`](https://docs.ansible.com/projects/lint/usage/) will be run,
make sure your branch passes this or the merge request will not be approved. the `ansible-lint` package is available on PyPi

## `<config>.yaml` format
The format of the dashboard `.yaml` configuration is as follows
```yaml
---
dashboards:
  <name of your dashboard>:
    # gatus config goes straight in here
```

that's it! nothing more is required.


## Rules
- Keep your probe intervals above two seconds (this applies to everything apart from domain expiration probes)
- domain expiration probe intervals are at the most frequent, allowed to run at 30 minute intervals
  (See more info here: https://github.com/TwiN/gatus?tab=readme-ov-file#monitoring-domain-expiration)

## Alerts?

Alerts are coming very soon. Thermia will shim auth details for an smtp server into your gatus config through the deploy pipeline.

## Issues?

Feel free to open issues on the repo if there are any questions!
