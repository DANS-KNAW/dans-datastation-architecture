Dataverse
=========

> "The Dataverse Project is an open source web application to share, preserve, cite, explore, and analyze research
> data."

In the Data Station this repository system is used for depositing, storing and disseminating datasets, as well as
creating long-term preservation copies of those datasets.

## Workflows

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

[Dataverse]: {{ dataverse_docs }}
[Workflows]: https://guides.dataverse.org/en/latest/developers/workflows.html#workflows
[RDA's BagPack recommendation]: {{ bagpack_specs }}
