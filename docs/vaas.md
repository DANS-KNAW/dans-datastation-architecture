Vault as a Service
==================

Overview
---------

Clients can also use the DANS Data Vault as a building block in their own archival workflows. To this end DANS offers **Vault as a Service**. It exposes the
same SWORD2 interface as the Data Stations. Instead of storing the datasets in Dataverse, they are directly converted into BagPacks and transferred to the Data
Vault. In this scenario, curation as well as dissemination of the datasets remain the responsibility of the customer.

[![Overview](arch-overview-vaas.png)<button class="btn">Enlarge Image</button>](arch-overview-vaas.png){: data-lightbox="group" data-title="Overview" }

Components
----------

The "Vault as a Service" configuration has mostly the same components as a Data Station. The main difference is that Dataverse is not part of the configuration.
Instead, a new component, [dd-vault-ingest]{:target=_blank}, is introduced to convert the datasets into RDA compliant bags and transfer them to the Data Vault.

[dd-vault-ingest]: dans-microservices.md#dd-vault-ingest
