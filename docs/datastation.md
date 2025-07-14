Data Station architecture
=========================

Overview
--------
This document gives an overview of the Data Station architecture. The schema below displays the components of a Data
Station and how they relate to each other. The notation used is not a formal one and is intended to be self-explanatory.
To the extent that it is not, you might want to consult
the [legend that is included at the end of this page](#schema-legend).

[![Overview](arch-overview.png)<button class="btn">Enlarge Image</button>](arch-overview.png){: data-lightbox="group" data-title="Overview" }


Actors
------

* **Data Station User** - a user of the Data Station, typically a customer who downloads or deposits data.
* **Data Manager** - a user with special privileges, who curates and publishes datasets submitted for review by a user.
* **SWORD2 Client** - a software client that interacts with the [DANS SWORD2 Service](#dd-sword2) to deposit datasets.

Components
----------

### Dataverse

> "The Dataverse Project is an open source web application to share, preserve, cite, explore, and analyze research
> data."

In the Data Station this repository system is used for depositing, storing and disseminating datasets, as well as
creating long-term preservation copies of those datasets.

#### Workflows

Dataverse provides event hooks that allow to configure workflows to run just before and after a publication event. These
workflows can have multiple steps. A step can be implemented as part of Dataverse or as an external service. The
following microservices are configured to run as `PrePublishDataset` workflow steps:

* [dd-vault-metadata](#dd-vault-metadata)

The following microservices are candidates to become part of the `PrePublishDataset` workflow in the future:

* [dd-virus-scan](#dd-virus-scan)

The **BagPack export** flow step is implemented in Dataverse and is used to create an export of the published dataset version (a "Dataset Version Export" or
DVE). The export complies with the [RDA's BagPack recommendation]{:target=_blank}. This exported bag is then picked up
by [dd-transfer-to-vault](#dd-transfer-to-vault).

| Docs                        | Code                                                |
|-----------------------------|-----------------------------------------------------|
| [Dataverse]{:target=_blank} | <https://github.com/IQSS/dataverse>{:target=_blank} |
| [Workflows]{:target=_blank} | Part of the Dataverse code base                     |

[RDA's BagPack recommendation]: {{ rda_research_data_repo_interoperability_wg_recommendations }}





Libraries
---------

The components mentioned above use many open source libraries. A couple of these are developed by DANS and are available
on GitHub.

| Library                                     | Code                                                                     |
|---------------------------------------------|--------------------------------------------------------------------------|
| [dans-bagit-lib]{:target=_blank}            | <https://github.com/DANS-KNAW/dans-bagit-lib>{:target=_blank}            |    
| [dans-dataverse-client-lib]{:target=_blank} | <https://github.com/DANS-KNAW/dans-dataverse-client-lib>{:target=_blank} |
| [dans-java-utils]{:target=_blank}           | <https://github.com/DANS-KNAW/dans-java-utils>{:target=_blank}           |
| [dans-validation-lib]{:target=_blank}       | <https://github.com/DANS-KNAW/dans-validation-lib>{:target=_blank}       |
| [dans-converter-lib]{:target=_blank}        | <https://github.com/DANS-KNAW/dans-converter-lib>{:target=_blank}        |

Schema Legend
-------------
[![Legend](legend.png)<button class="btn">Enlarge Image</button>](legend.png){: data-lightbox="group" data-title="Legend" }

[dans-bagit-lib]: https://dans-knaw.github.io/dans-bagit-lib

[dans-dataverse-client-lib]: https://dans-knaw.github.io/dans-dataverse-client-lib

[dans-java-utils]: https://dans-knaw.github.io/dans-java-utils

[dans-validation-lib]: https://dans-knaw.github.io/dans-validation-lib

[dans-converter-lib]: https://dans-knaw.github.io/dans-converter-lib

[Dataverse]: {{ dataverse_docs }}

[Workflows]: https://guides.dataverse.org/en/latest/developers/workflows.html#workflows

[dd-sword2]: https://dans-knaw.github.io/dd-sword2/

[dd-dans-sword2-examples]: https://dans-knaw.github.io/dd-dans-sword2-examples/

[dd-dataverse-authenticator]: https://dans-knaw.github.io/dd-dataverse-authenticator/

[dd-dataverse-ingest]: https://dans-knaw.github.io/dd-dataverse-ingest

[dd-validate-dans-bag]: https://dans-knaw.github.io/dd-validate-dans-bag

[dd-manage-deposit]: https://dans-knaw.github.io/dd-manage-deposit

[DANS BagIt Profile v1]: {{ dans_bagit_profile }}

[DANS schema]: https://dans-knaw.github.io/dans-schema/

[dans-datastation-tools]: https://dans-knaw.github.io/dans-datastation-tools

[http/authext]: https://guides.dataverse.org/en/latest/developers/workflows.html#http-authext

[dd-virus-scan]: https://dans-knaw.github.io/dd-virus-scan

[dd-vault-metadata]: https://dans-knaw.github.io/dd-vault-metadata

[dd-vault-catalog]:  https://dans-knaw.github.io/dd-vault-catalog

[dd-data-vault]: https://dans-knaw.github.io/dd-data-vault

[dd-data-vault-cli]: https://dans-knaw.github.io/dd-data-vault-cli

[dd-transfer-to-vault]:  https://dans-knaw.github.io/dd-transfer-to-vault

[Skosmos]: {{ skosmos_url }}

[SURF Data Archive]: https://servicedesk.surf.nl/wiki/display/WIKI/Data+Archive

[OCFL]: https://ocfl.io/

[NBN]: https://www.ifla.org/references/best-practice-for-national-bibliographic-agencies-in-a-digital-age/resource-description-and-standards/identifiers/national-bibliography-number-nbn/

[Koninklijke Bibliotheek]: https://www.kb.nl/en