External interfaces
===================

The following interfaces are exposed to the outside world:

* The **[Dataverse user interface]{:target=_blank}**. This interface used by human users.
* The **[Dataverse RESTful HTTP API]{:target=_blank}**. This interface is used by internal and external systems that need to interact with Dataverse.
* A **[SWORD2 deposit service]**. S This interface is used by external systems that want to deposit data in Dataverse or directly in the Data Vault.
* Long term preservation copies of the data via the **[Data Vault Storage Root]**. This interface (or exchange format) is intended for future users who need to
  disseminate the data stored in the Data Vault after the current dissemination infrastructure has been decommissioned.

[SWORD2 deposit service]: ./sword.md

[Dataverse user interface]: {{ dataverse_user_guide }}
[Dataverse RESTful HTTP API]: {{ dataverse_api_guide }}
[Data Vault Storage Root]: ./data-vault-storage-root.md
