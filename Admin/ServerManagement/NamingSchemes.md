# Server Naming Schemes
> Part of [Administration](/Admin/Index.md) / [Server Management](/Admin/ServerManagement/Index.md)

Newly provisioned servers must be named in a consistent, predictable manner according to their primary client, the infrastructure in which they are contained, and their logical order within any sets. The exception to this is:

 - Ephemeral servers created as part of a cluster
 - Existing or legacy servers not on either AWS, Azure or DigitalOcean.

The naming of a server should be as follows:

```
	<client>-<service[-product]>-<index>
```

Comprising of the following components:

 - `client` — Brief client name
 - `service` — Such as `aws`, `azure` etc.
 - `product` — An optional product name if the service provides more than one product for single VM instances, such as `ec2`, `lambda`, `rds` etc.
 - `index` — Starting at `01`, the numeric index of the server. Required even if there is only one server.

An example would for a pair of servers on AWS EC2 would be:

```
widgetsco-aws-ec2-01
widgetsco-aws-ec2-01
```

And a single of server on Azure would be:

```
widgetsco-azure-vm-01
```

## Domain names
Domains pointing to the relevant servers will be formatted as such:

```
	<client>-<index>.<service-product>.wsdev.org
```

These are not public or client facing domains, and if there is a requirement for such a domain, it will be created in accordance with the standard `client-project[.test|stage].wsdev.org` scheme.

## Service reference

The following services and their short names can be used:

 - AWS (`aws`)
   - EC2 (`aws-ec2`); RDS (`aws-rds`)
 - Azure (`azure`)
   - Azure VMs (`azure-vm`)
 - DigitalOcean (`do`)
   - Droplet (`do-drop`)
 - IOMart (`iomart`)
 - DataVita (`dv`)
 - China Net Cloud (`cnc`)