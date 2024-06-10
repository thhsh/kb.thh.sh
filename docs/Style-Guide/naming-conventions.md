# Naming Conventions
## File Naming Conventions
### Overview
Overall, file and directory names should follow a *slightly modified* version of **kebab-case**. 

-   Words are written in lowercase[^1].
-   Spaces within titles are repaced with a hyphen `-`.
-   Sections can be separated with an underscore `_`.
-   When reasonable, begin the file name with the modified [date](#dates), to allow for easier sorting.
-   Version or revision numbers, where necessary, are written with a lowercase `v#` or `r#`.
    -   When the revision or version number is a single digit, include a leading `0` to keep sorting friendly across different platforms.

| Do | Don't |
| --- | -- |
| `cool-arena_graphics-config` | `Graphics Config - Cool Arena` |
| `2024-06-10_cool-arena_graphics-config_v6` | `Cool Arena - Graphics Config - 6/10/24 - final` |
| `cool-arena\graphics-config_r06` | `Cool Arena\Graphics Config - final` |
| `Style-Guide\naming-conventions.md`[^1] | `styleguide\naming_conventions.md`[^1] |

### Dates
Dates are written in [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format, which is `YYYY-MM-DD`.

| Do | Don't |
| -- | ----- |
| `2024-06-10` | `6/10/24` |
| `2024-06-10` | `June 10th, 2024` |
| `2024-06-10` | `10 Jun 2024` |

## Server/Computer Naming Conventions
### Server Naming Conventions
Servers are named with the following convention: `Environment - Provider - Datacenter - Type - OS - Purpose - Sequential number`

#### Environment
| Slug | Environment | Notes |
| ---- | ----------- | ----- |
| `PROD` | Production | |
| `STG` | Staging | |
| `DEV` | Development | |
| `TEST` | Testing use only | Typically ephemeral machines |


#### Provider
Commonly used providers:

| Slug | Provider | Services |
| ---- | -------- | -------- |
| `HTZ` | [:simple-hetzner: Hetzner](https://www.hetzner.com/) | VPS, Dedicated Servers, Storage |
| `DO` | [:material-digital-ocean: DigitalOcean](https://www.digitalocean.com/) | VPS, Storage, App Platform |
| `BVM` | [:material-horse-variant: BuyVM/Frantech](https://buyvm.net) | VPS, Storage |
| `VLTR` | [:simple-vultr: Vultr](https://www.vultr.com/) | VPS |

#### Datacenter
Datacenters for commonly used providers:

| Provider | Datacenters |
| -------- | ----------- |
| :simple-hetzner: Hetzner | [Hetzner - Locations](https://docs.hetzner.com/cloud/general/locations/) |
| :material-digital-ocean: DigitalOcean | [DigitalOcean - Regional Availability](https://docs.digitalocean.com/platform/regional-availability/) |
| :material-horse-variant: BuyVM | [BuyVM - Datacenters](https://buyvm.net/datacenters/) |
| :simple-vultr: Vultr | [Vultr - Locations](https://www.vultr.com/features/datacenter-locations/) |

#### Type
| Slug | Type |
| ---- | ---- |
| `VPS` | VPS, Virtual Private Server |
| `DEDI` | Dedicated hosted server |
| `COLO` | Colocated server owned by us |

#### OS
| Slug | OS |
| ---- | -- |
| `UBT` | :simple-ubuntu: Ubuntu |
| `DEB` | :material-debian: Debian |
| `ALP` | :simple-alpinelinux: Alpine Linux |
| `WIN` | :simple-windows11: Windows |
| `MAC` | :material-apple: MacOS |

#### Examples
| Name | Description |
| ---- | ----------- |
| `DEV-BVM-NJ-VPS-UBT-Teleport-01` | Development VPS, hosted by Frantech/BuyVM in their  datacenter, Ubuntu OS, running Teleport |
| `STG-DO-NYC1-VPS-UBT-Ghost-03` | Staging VPS, hosted by DigitalOcean in their NYC1 datacenter, Ubuntu OS, running Ghost |
| `PROD-HTZ-HEL1-DEDI-DEB-NextCloud-02` | Production Dedicated server, hosted by Hetzner in their Helsinki FI datacenter, Debian OS, running NextCloud |

[^1]:
    **Important caveat for titles in lowercase:**  
    Due to limitations in how MkDocs processes directory names, directory names that are being used as "sections" or "directories" in Material for MkDocs should be written in **Title Case**. (Otherwise, only the first word of the directory will be capitalized in site navigation. [See Github discussion here](https://github.com/mkdocs/mkdocs/issues/1289#issuecomment-331021585).)