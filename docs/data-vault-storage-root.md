Data Vault Storage Root
=======================

Introduction
------------

The Data Vault is subdivided into **Storage Roots**, containing the long-term preservation copies for Data Stations and "Vault as a Service" (VaaS) customers.
The Data Vault Storage Root (DVSR) can be viewed as a type of interface, or exchange format, albeit an atypical one, as it is aimed at future users, rather than
current ones.

!!! alert "dd-data-vault interface"

    Do not confuse the DVSR with the [service interface of dd-data-vault], which is an internal microservice interface that is used by the [transfer service] to 
    store data in the Data Vault.

[service interface of dd-data-vault]: dans-microservices.md#dd-data-vault

[transfer service]: dans-microservices.md#dd-transfer-to-vault


OCFL repositories
-----------------
The DANS Data Vault is implemented as an array of **OCFL** repositories. OCFL stands for [Oxford Common File Layout]{:target=_blank}. It is a community
specification for the layout of a repository that stores versioned digital objects. Each repository, or "storage root," is one
**Data Vault Storage Root (DVSR)**. The Data Stations each have their own DVSR as does each customer of the Vault as a Service.

### Extensions

OCFL can be extended with additional metadata and functionality. The DANS Data Vault uses the following extensions:

* [Object Version Properties]{:target=_blank} - This extension defines a way to specify properties for each version of an object.
* [Property Registry]{:target=_blank} - This extension defines a registry for properties that can be used in the Object Version Properties extension.
* [OCFL Packaging Format Registry]{:target=_blank} - This extension defines a list of packaging formats. Packging formats specify the internal structure of an
  archived dataset version export.

[Object Version Properties]: {{ object_version_properties }}
[Property Registry]: {{ property_registry }}
[OCFL Packaging Format Registry]: {{ packaging_format_registry }}

Dataset model mapping
---------------------

OCFL is a generic storage model. It does not define the concept of a dataset. The DANS archival systems (Data Stations and Vault as a Service), on the other
hand, are built around the dataset concept. It is essential that the datasets stored in the Vault can be reconstructed from the OCFL objects. For this purpose
this section documents the mapping between the two models.

### Basic mapping scheme

The basic mapping scheme is concerned with reconstructing datasets and their version history from OCFL objects.

| DANS dataset model | OCFL model          | Multiplicity |
|--------------------|---------------------|--------------|
| Dataset            | OCFL Object         | 1-to-1       |
| Dataset Version    | OCFL Object Version | 1-to-1..*    |
| Datafile           | OCFL Content File   | 1-to-1       |

### Versions vs Version Exports

Each Dataset Version is exported from Dataverse (or from the VaaS client's own system) and stored in a separate OCFL Object Version. This means that there is a
1-to-1 mapping between a Dataset Version Export and an OCFL Object Version. Note, however, that it is possible that one Dataset Version is exported multiple
times. The mapping of a dataset version to an OCFL Object is therefore a 1-to-_n_ relationship (with _n > 0_)

!!! note "A multiple exports scenario"

    A scenario where a dataset version is exported multiple times is when the dataset was updated in the Data Station without creating a new version. This can 
    be done by a superuser and is known as **"updatecurrent"**. A new Dataset Version Export will be created and therefore a new OCFL Object Version will be 
    created as well. The Data Station version history, however, will **not** display an additional version.

### Making sense of a version export

Apart from determining now a series of Data Version Exports constitute the version history of a dataset, it is also important to be able to interpret each
individual DVE correctly. Over time, the way datasets are exported may change. For example, the layout of the exported files and the metadata included may be
different. That is why each OCFL Object Version has a packaging format attribute.

!!! note "BagPack"

    The current packaging format is called **[BagPack]{:target=_blank}**. It is a recommendation by the Research Data Alliance (RDA) and is implemented as an 
    export/import format by Dataverse. For VaaS, DANS has implement BagPack to closely resemble the Dataverse implementation.

[BagPack]: {{ bagpack_specs }}

### Structural attributes

The following diagram gives an overview of the structural attributes and how they are mapped to the OCFL model.

Key to the columns:

* **DANS Dataset Model**: how DANS conceptualizes datasets. This includes both Dataverse and VaaS datasets.
* **Dataset Version Exports**: the relevant properties of the exported datasets versions.
* **OCFL Model**: how OCFL conceptualizes objects and their versions. Note that the attributes marked with `)*` are custom version properties defined using the
  [Object Version Properties](#extensions) extension.

![Vault metadata](vault-metadata.png){: .align-center}

The following table makes explicit where the various attributes originate from and what their purpose is.

| Attribute                  | Source                                | Purpose                                                    |
|----------------------------|---------------------------------------|------------------------------------------------------------|
| ID of the OCFL Object      | NBN of the dataset (assigned by DANS) | Uniquely identifying the dataset in the Vault              |
| OCFL Object Version Number | Sequential number assigned by OCFL    | Identifying OCFL Object Version within its parent Object   |
| dataset.major-version      | Major version number                  | Establishing the version history of the original dataset   |
| dataset.minor-version      | Minor version number                  | Establishing the version history of the original dataset   |
| dataset.export-number      | Nth export of the dataset version     | Establishing the version history of the original dataset   |
| packaging-format           | Packaging format used for the DVE     | Recording the layout of the contents of the Object Version |

[bag]: {{ bagit_specs }}
[Oxford Common File Layout]: {{ ocfl_url }}

Serialization in layers
-----------------------

OCFL repositories can be serialized in different ways, for example as a directory structure on a file system, or as objects in an object store. The DANS Data
Vault uses the SURF [Data Archive]{:target=_blank} tape storage. The tape storage system that is used by Data Archive organizes files in a file-folder
structure, so in principle serialization should be the same as to a disk-based files system, from OCFL's perspective. However, the tape storage system requires
a minimum file size of 1GB, which is much larger than the typical data file stored in the DANS Data Vault. To meet this requirement, the OCFL repositories are
stored as a series of DMFTAR archives, each of which is larger than 1GB. Each archive forms a layer. For a more detailed description of the layers, see the
documentation of [dans-layer-store-lib]{:target=_blank}.

To restore the OCFL repository, the layers must be extracted in the correct order. SURF provides a utility called [dmftar]{:target=_blank} to create and extract
DMFTAR archives. This utility is the interface to the tape storage system.

!!! alert "Restoring without the `dmftar` utility"

    Even without the `dmftar` utility, it is possible to restore the OCFL repository, as long as the layers are extracted in the correct order. A DMFTAR archive 
    is just a lightweight wrapper around a TAR archive, implemented as a directory containing batches of (possibly multi-volume) TAR files along with index 
    files and a checksum file.

[dans-layer-store-lib]: dans-libraries.md#dans-layer-store-lib
[Data Archive]: {{ data_archive }}
[dmftar]: {{ dmftar }}
