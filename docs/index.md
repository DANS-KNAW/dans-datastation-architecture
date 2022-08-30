DANS Data Station Architecture
==============================

Overview
--------
This document gives an overview of the DANS Data Station architecture. The schema below displays all the components of a Data Station and how they relate to
each other. The notation used is not a formal one and attempts to be self-explanatory. To the extent that
A [legend is included at the end of this page](#schema-legend).

![Overview](arch-overview.png)

Components
----------

### Dataverse

> "The Dataverse Project is an open source web application to share, preserve, cite, explore, and analyze research data."

In the Data Station this repository system is used for depositing, storing and disseminating datasets, as well as creating long-term preservation copies of
those datasets.

| Docs                         | Code                                                |
|------------------------------|-----------------------------------------------------|
| [Dataverse]{:target=_blank}  | <https://github.com/IQSS/dataverse>{:target=_blank} |
| [Workflows]{:target=_blank}  |                                                     |

### dd-sword2

DANS implementation of the SWORD v2 protocol for automated deposits.

| Docs                        | Code                                                     |
|-----------------------------|----------------------------------------------------------|
| [dd-sword2]{:target=_blank} | <https://github.com/DANS-KNAW/dd-sword2>{:target=_blank} |

### dd-ingest-flow

| Docs                             | Code                                                          |
|----------------------------------|---------------------------------------------------------------|
| [dd-ingest-flow]{:target=_blank} | <https://github.com/DANS-KNAW/dd-ingest-flow>{:target=_blank} |

[Dataverse]: https://guides.dataverse.org/en/latest/user/index.html

[Workflows]: https://guides.dataverse.org/en/latest/developers/workflows.html#workflows

[dd-sword2]: https://dans-knaw.github.io/dd-sword2/

[dd-ingest-flow]: https://dans-knaw.github.io/dd-ingest-flow

[dans-datastation-tools]: https://dans-knaw.github.io/dans-datastation-tools



Schema Legend
-------------

