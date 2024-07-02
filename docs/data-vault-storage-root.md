Data Vault Storage Root
=======================

Introduction
------------

The Data Vault is subdivided into **Storage Roots**, each one containing the long term preservation copies for either a Data Station or a "Vault as a
Service"  (VaaS) customer. A Data Vault Storage Root (DVSR) can be viewed as a type of interface, or exchange format, albeit an atypical one, as it is aimed at
future users, rather than current ones.

!!! alert "dd-data-vault interface"

    Do not confuse the DVSR with the of [service interface dd-data-vault], wich is an internal microservice interface that is used by the ingest pipeline to 
    store data in the Data Vault.

[service interface dd-data-vault]: /datastation#dd-data-vault

OCFL repositories
-----------------

The DANS Data Vault is implemented as an array of **OCFL** repositories. OCFL stands for [Oxford Common File Layout]{:target=_blank}. It is a community
specification for the layout of a repository that stores versioned digital objects. Each repository, or "storage root," is one
**Data Vault Storage Root (DVSR)**. The Data Stations each have their own DVSR as does each customer of the Vault as a Service.

### Layers

The DVSRs are not stored as regular directories on a regular file system, but instead packaged in DMF TAR files. This is because the tape storage system that is
used, requires a minimum file size of 1GB. Parts of the repository therefore need to be combined into a single file to meet this requirement. Each TAR file
constitutes a layer. To unpack a DVSR, its layer files must be extracted in the correct order. The base name of each layer file is a Unix timestamp with
millisecond precision. The order of extraction is the chronological order of the timestamps. This is important because, layers in later layer files may contain
files that overwrite files in earlier layers, notably the `inventory.json` files.

For a more detailed description of the layers, see the documentation of [dans-layer-store-lib]{:target=_blank}.

!!! note "DMF TAR"

    The Data Vault is stored in SURF's **[Data Archive]{:target=_blank}**, which uses DMF as its tape storage system. DMF stands for **Data Migration Facility**.
    SURF has developed a utility called **[dmftar]{:target=_blank}**: _"dmftar is a wrapper for the Linux tool gnutar and automatically creates multi-volume 
    archive files (...) and can incorporate the transfer of the files to the archive file system if necessary."_  `dmftar` stores the TAR volumes in a directory
    with the extension `.dmftar`, which also contains an index and a checksum file.

[dans-layer-store-lib]: {{ dans_layer_store_lib }}
[Data Archive]: {{ data_archive }}
[dmftar]: {{ dmftar }}

Dataset model mapping
---------------------

OCFL is a generic storage model. It does not define the concept of a dataset. The DANS archival systems (Data Stations and Vault as a Service), on the other
hand, are built around the dataset concept. The mapping between the two models is as follows:

| DANS dataset model | OCFL model          |
|--------------------|---------------------|
| Dataset            | OCFL Object         |
| Dataset Version    | OCFL Object Version |
| Datafile           | OCFL Content File   |

### Versions

Each Dataset Version Export (DVE) is stored in a separate OCFL Object Version. This means that there is a 1-to-1 mapping between a DVE and an OCFL Object
Version. Note however, that it is possible that one dataset version is exported multiple times. The mapping of a dataset version to an OCFL Object is therefore
a 1-to-_n_ relationship.

!!! note "Multiple exports"

    A scenario where a dataset version is exported multiple times is when the dataset was updated in the Data Station without creating a new version. This can 
    be done by a superuser and is known as **"updatecurrent"**. A new Dataset Version Export will be created and therefore a new OCFL Object Version will be 
    created as well. The Data Station version history, however, will **not** display an additional version.

### Metadata






[bag]: {{ bagit_specs }}
[Oxford Common File Layout]: {{ ocfl_url }}