Data Vault
==========

Introduction
------------

It may be surprising to talk about the Data Vault's **interface**. However, viewed from the standpoint of a future user of our long-term preservation copies,
the details of how to retrieve the information stored in the Data Vault are essential. It is that interface that we describe here.

The Data Vault interface is classified here as an **internal** interface, but it could arguably be classified as an external interface as well, particularly in
a scenario where a future, external organization is responsible for taking up the dissemination of the data stored in the Data Vault. Nevertheless, for the time
being, we consider it an internal interface, as it is currently only used by DANS systems.

Data Vault Storage Roots
------------------------

The DANS Data Vault is implemented as an array of [OCFL]{:target=_blank} repositories. OCFL stands for Oxford Common File Layout. It is a community
specification for the layout of a repository that stores versioned digital objects. Each repository, or "storage root," is one **Data Vault Storage Root**. The
Data Stations each have their own Data Vault Storage Root as does each customer of the Vault as a Service.

### Layers

The Data Vault Storage Roots are not stored as regular directories on a regular file system, but instead packaged in DMF TAR files. This is because the tape
storage system that is used, requires a minimum file size of 1GB. Parts of the repository therefore need to be combined into a single file to meet this
requirement. Each TAR file constitutes a layer. To restore a Data Vault Storage Root, the layer TAR files must be extracted in the correct order. The base name
of each layer TAR file is a Unix timestamp with millisecond precision. The order of extraction is the chronological order of the timestamps. This is important
because, layers in later TAR files may contain files that overwrite files in earlier layers, notably the `inventory.json` files.

For a more detailed description of the layers, see the documentation of [dans-layer-store-lib]{:target=_blank}.

[dans-layer-store-lib]: {{ dans_layer_store_lib }}

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

Some scenarios where a dataset version is exported multiple times are:

* The dataset was updated in the Data Station without creating a new version. This can be done by a superuser and is known as "updatecurrent". A new Dataset
  Version Export will be created and therefore a new OCFL Object Version will be created as well. The Data Station version history, however, will **not**
  display an additional version.
* Repackaging of one or all of the Dataset Version Exports. Currently, the DVEs are store in a [bag]{:target=_blank} that complies with recommendations
  published by the Research Data Alliance. If at some time in the future, a new packaging format should be adopted, the DVEs will be repacked. Since the OCFL
  repository is immutable, the repacking will result in a new OCFL Object Version(s) being created.

### Metadata






[bag]: {{ bagit_specs }}
[OCFL]: {{ ocfl_url }}