DANS Microservices
==================

Several of the components in the architecture are implemented as microservices and developed by DANS. Microservice projects often have an associated API
project, containing the OpenAPI specification as well as a Command Line Interface (CLI) project that provides a command line tool for interacting with the
microservice. Note, that the head of the API project is not necessarily the version implemented by the microservice, but rather the latest version of the
OpenAPI specification.

## dd-confirm-archiving

Monitors dataset version exports that are being archived and registers the archival timestamp in the [Vault Catalog] once the export is archived in the DANS
Data Vault.

| Docs                                       | Code                                                                    |
|--------------------------------------------|-------------------------------------------------------------------------|
| [dd-confirm-archiving]{:target=_blank}     | <https://github.com/DANS-KNAW/dd-confirm-archiving>{:target=_blank}     |
| [dd-confirm-archiving-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-confirm-archiving-api>{:target=_blank} |

[dd-confirm-archiving]: https://dans-knaw.github.io/dd-confirm-archiving/

[dd-confirm-archiving-api]: https://dans-knaw.github.io/dd-confirm-archiving-api/

[Vault Catalog]: #dd-vault-catalog

## dd-data-vault

Service that manages a [Data Vault Storage Root] and provides a REST API for interacting with it.

[Data Vault Storage Root]: ../data-vault-storage-root/

| Docs                                | Code                                                             |  
|-------------------------------------|------------------------------------------------------------------|
| [dd-data-vault]{:target=_blank}     | <https://github.com/DANS-KNAW/dd-data-vault>{:target=_blank}     |
| [dd-data-vault-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-data-vault-api>{:target=_blank} |
| [dd-data-vault-cli]{:target=_blank} | <https://github.com/DANS-KNAW/dd-data-vault-cli>{:target=_blank} |

[dd-data-vault]: https://dans-knaw.github.io/dd-data-vault/

[dd-data-vault-api]: https://dans-knaw.github.io/dd-data-vault-api/

[dd-data-vault-cli]: https://dans-knaw.github.io/dd-data-vault-cli/

## dd-dataverse-authenticator

A proxy that authenticates clients on behalf of Dataverse, using the basic auth protocol or a Dataverse API token. It is
used by [dd-sword2](#dd-sword2) to authenticate its clients by their Dataverse account credentials.

| Docs                                         | Code                                                                      |
|----------------------------------------------|---------------------------------------------------------------------------|
| [dd-dataverse-authenticator]{:target=_blank} | <https://github.com/DANS-KNAW/dd-dataverse-authenticator>{:target=_blank} |

[dd-dataverse-authenticator]: https://dans-knaw.github.io/dd-dataverse-authenticator/

## dd-dataverse-cli

Command line tool for interacting with the [Dataverse] service. It uses [dans-dataverse-client-lib] to communicate with the Dataverse API.

| Docs                                         | Code                                                                      |
|----------------------------------------------|---------------------------------------------------------------------------|
| [dd-dataverse-authenticator]{:target=_blank} | <https://github.com/DANS-KNAW/dd-dataverse-authenticator>{:target=_blank} |

[Dataverse]: ../dataverse/

[dans-dataverse-client-lib]: ../dans-libraries/#dans-dataverse-client-lib

Note, this will replace most of the old [dans-datastation-tools]{:target=_blank} command line tools, which are now deprecated.

[dans-datastation-tools]: https://dans-knaw.github.io/dans-datastation-tools/

## dd-dataverse-ingest

Service for ingesting [deposit directories](./deposit-directory.md) into Dataverse.

| Docs                                      | Code                                                                   |
|-------------------------------------------|------------------------------------------------------------------------|
| [dd-dataverse-ingest]{:target=_blank}     | <https://github.com/DANS-KNAW/dd-dataverse-ingest>{:target=_blank}     |
| [dd-dataverse-ingest-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-dataverse-ingest-api>{:target=_blank} |
| [dd-dataverse-ingest-cli]{:target=_blank} | <https://github.com/DANS-KNAW/dd-dataverse-ingest-cli>{:target=_blank} |

[dd-dataverse-ingest]: https://dans-knaw.github.io/dd-dataverse-ingest/

[dd-dataverse-ingest-api]: https://dans-knaw.github.io/dd-dataverse-ingest-api/

[dd-dataverse-ingest-cli]: https://dans-knaw.github.io/dd-dataverse-ingest-cli/

## dd-gmh

Command line tool for interacting with the [BRI-GMH resolver](#bri-gmh) to resolve a DANS Persistent Identifier (NBN) to a URL.

| Docs                         | Code                                                                                            |
|------------------------------|-------------------------------------------------------------------------------------------------|
| [dd-gmh-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-gmh-api>{:target=_blank}                                       |
| In code                      | <https://persistent-identifier.nl/gmh-registration-service/api/v1/openapi.yaml>{:target=_blank} |
| [dd-gmh-cli]{:target=_blank} | <https://github.com/DANS-KNAW/dd-gmh-cli>{:target=_blank}                                       |

Note, that the GMH used to be maintained by DANS, but is currently maintained and hosted by Seecr on behalf of the Koninklijke Bibliotheek (KB).
The `dd-gmh-api` project contains a copy of the OpenAPI specification to be used in the build process of the `dd-gmh-cli` project. The authoritative OpenAPI
specification is published at <https://persistent-identifier.nl/gmh-registration-service/api/v1/openapi.yaml>{:target=_blank}.


[dd-gmh-api]: https://dans-knaw.github.io/dd-gmh-api/

[dd-gmh-cli]: https://dans-knaw.github.io/dd-gmh-cli/

## dd-manage-deposit

Service that manages and maintains information about deposits in a deposit area.

| Docs                                    | Code                                                                 |
|-----------------------------------------|----------------------------------------------------------------------|
| [dd-manage-deposit]{:target=_blank}     | <https://github.com/DANS-KNAW/dd-manage-deposit>{:target=_blank}     |
| [dd-manage-deposit-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-manage-deposit-api>{:target=_blank} |
| [dd-manage-deposit-cli]{:target=_blank} | <https://github.com/DANS-KNAW/dd-manage-deposit-cli>{:target=_blank} |

Note, that the current implementation of `dd-manage-deposit` does not yet implement `dd-manage-deposit-api` and `dd-manage-deposit-cli`, but instead has a
manually coded API and CLI.

[dd-manage-deposit]: https://dans-knaw.github.io/dd-manage-deposit/

[dd-manage-deposit-api]: https://dans-knaw.github.io/dd-manage-deposit-api/

[dd-manage-deposit-cli]: https://dans-knaw.github.io/dd-manage-deposit-cli/

## dd-sword2

DANS implementation of the SWORD v2 protocol for automated deposits.

| Docs                                      | Code                                                                   |
|-------------------------------------------|------------------------------------------------------------------------|
| [dd-sword2]{:target=_blank}               | <https://github.com/DANS-KNAW/dd-sword2>{:target=_blank}               |
| [dd-dans-sword2-examples]{:target=_blank} | <https://github.com/DANS-KNAW/dd-dans-sword2-examples>{:target=_blank} |

[dd-sword2]: https://dans-knaw.github.io/dd-sword2/

[dd-dans-sword2-examples]: https://dans-knaw.github.io/dd-dans-sword2-examples/

## dd-transfer-to-vault

Service for preparing Dataset Version Exports for storage in the [DANS Data Vault](#dd-data-vault). This includes validation, registering the NBN for a
dataset with the [BRI-GMH resolver](#bri-gmh), creating a [vault catalog](#dd-vault-catalog) entry and handing over the bag to
the [dd-data-vault](#dd-data-vault) service.

| Docs                                   | Code                                                                |
|----------------------------------------|---------------------------------------------------------------------|
| [dd-transfer-to-vault]{:target=_blank} | <https://github.com/DANS-KNAW/dd-transfer-to-vault>{:target=_blank} |

[dd-transfer-to-vault]: https://dans-knaw.github.io/dd-transfer-to-vault/

## dd-validate-bagpack

Service that checks whether a bag complies with the [BagPack specification]{:target=_blank}.

| Docs                                  | Code                                                               |
|---------------------------------------|--------------------------------------------------------------------|
| [dd-validate-bagback]{:target=_blank} | <https://github.com/DANS-KNAW/dd-validate-bagback>{:target=_blank} |

**NOT YET IMPLEMENTED**

[dd-validate-bagback]: https://dans-knaw.github.io/dd-validate-bagback/

[BagPack specification]: {{ bagpack_specs }}

## dd-validate-dans-bag

Service that checks whether a bag complies with DANS BagIt Profile v1. It is used by [dd-dataverse-ingest](#dd-dataverse-ingest)
to validate bags that are uploaded via [dd-sword2](#dd-sword2).

| Docs                                       | Code                                                                    |
|--------------------------------------------|-------------------------------------------------------------------------|
| [dd-validate-dans-bag]{:target=_blank}     | <https://github.com/DANS-KNAW/dd-validate-dans-bag>{:target=_blank}     |
| [dd-validate-dans-bag-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-validate-dans-bag-api>{:target=_blank} |
| [dd-validate-dans-bag-cli]{:target=_blank} | <https://github.com/DANS-KNAW/dd-validate-dans-bag-cli>{:target=_blank} |
| [DANS BagIt Profile v1]{:target=_blank}    | <https://github.com/DANS-KNAW/dans-bagit-profile>{:target=_blank}       | 
| [DANS schema]{:target=_blank}              | <https://github.com/DANS-KNAW/dans-schema>{:target=_blank}              | 

[dd-validate-dans-bag]: https://dans-knaw.github.io/dd-validate-dans-bag/

[dd-validate-dans-bag-api]: https://dans-knaw.github.io/dd-validate-dans-bag-api/

[dd-validate-dans-bag-cli]: https://dans-knaw.github.io/dd-validate-dans-bag-cli/

[DANS BagIt Profile v1]: https://dans-knaw.github.io/dans-bagit-profile/

[DANS schema]: https://dans-knaw.github.io/dans-schema/

## dd-vault-catalog

Service that manages a catalog of all Dataset Version Exports in the [DANS Data Vault]. It exposes a summary page for each stored dataset.

| Docs                                   | Code                                                                |
|----------------------------------------|---------------------------------------------------------------------|
| [dd-vault-catalog]{:target=_blank}     | <https://github.com/DANS-KNAW/dd-vault-catalog>{:target=_blank}     |
| [dd-vault-catalog-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-vault-catalog-api>{:target=_blank} |
| [dd-vault-catalog-cli]{:target=_blank} | <https://github.com/DANS-KNAW/dd-vault-catalog-cli>{:target=_blank} |

[dd-vault-catalog]: https://dans-knaw.github.io/dd-vault-catalog/

[dd-vault-catalog-api]: https://dans-knaw.github.io/dd-vault-catalog-api/

[dd-vault-catalog-cli]: https://dans-knaw.github.io/dd-vault-catalog-cli/

[DANS Data Vault]: ../data-vault-storage-root/

## dd-vault-ingest

Service for converting deposits coming in via Vault as a Service to BagPacks.

| Docs                              | Code                                                           |
|-----------------------------------|----------------------------------------------------------------|
| [dd-vault-ingest]{:target=_blank} | <https://github.com/DANS-KNAW/dd-vault-ingest>{:target=_blank} |

[dd-vault-ingest]: https://dans-knaw.github.io/dd-vault-ingest/

## dd-vault-metadata

A service that fills in the "Vault Metadata" for a dataset version. These metadata will be used later on by [dd-transfer-to-vault](#dd-transfer-to-vault) to
catalogue the long-term preservation copy of the dataset version when it is stored on tape.

| Docs                                    | Code                                                                 |
|-----------------------------------------|----------------------------------------------------------------------|
| [dd-vault-metadata]{:target=_blank}     | <https://github.com/DANS-KNAW/dd-vault-metadata>{:target=_blank}     |
| [dd-vault-metadata-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-vault-metadata-api>{:target=_blank} |

[dd-vault-metadata]: https://dans-knaw.github.io/dd-vault-metadata/

[dd-vault-metadata-api]: https://dans-knaw.github.io/dd-vault-metadata-api/

Note, that the current implementation of `dd-vault-metadata` does not yet implement `dd-vault-metadata-api`, but instead has a manually coded API.

## dd-virus-scan

A service that scans all files in a dataset for virus using `clamav` and blocks publication if a virus is found.

| Docs                                | Code                                                             |
|-------------------------------------|------------------------------------------------------------------|
| [dd-virus-scan]{:target=_blank}     | <https://github.com/DANS-KNAW/dd-virus-scan>{:target=_blank}     |
| [dd-virus-scan-api]{:target=_blank} | <https://github.com/DANS-KNAW/dd-virus-scan-api>{:target=_blank} |

Note, that the current implementation of `dd-virus-scan` does not yet implement `dd-virus-scan-api`, but instead has a manually coded API.

## dans-datastation-tools (deprecated)

Command line utilities for Data Station application management.

| Docs                                     | Code                                                                  |
|------------------------------------------|-----------------------------------------------------------------------|
| [dans-datastation-tools]{:target=_blank} | <https://github.com/DANS-KNAW/dans-datastation-tools>{:target=_blank} |

