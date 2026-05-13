Dataverse
=========

> "The Dataverse Project is an open source web application to share, preserve, cite, explore, and analyze research data."

In the Data Station this repository system is used for depositing, storing and disseminating datasets, as well as creating long-term preservation copies of
those datasets.

## Workflows

Dataverse provides event hooks that allow you to configure workflows to run just before and after a publication event. These workflows can have multiple steps.
A step can be implemented as part of Dataverse or as an external service. The following microservices are configured to run as `PrePublishDataset` workflow
steps:

* [dd-vault-metadata](dans-microservices.md#dd-vault-metadata)
* [dd-virus-scan](dans-microservices.md#dd-virus-scan)

| Docs                        | Code                                                |
|-----------------------------|-----------------------------------------------------|
| [Dataverse]{:target=_blank} | <https://github.com/IQSS/dataverse>{:target=_blank} |
| [Workflows]{:target=_blank} | Part of the Dataverse code base                     |

[Dataverse]: {{ dataverse_docs }}
[Workflows]: https://guides.dataverse.org/en/latest/developers/workflows.html#workflows
