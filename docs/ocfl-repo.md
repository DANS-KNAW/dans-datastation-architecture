OCFL repository
===============

The DANS Data Vault is implemented as an [OCFL]{:target=_blank} repository. OCFL stands for Oxford Common File Layout.
It is a community specification for the layout of a repository that stores digital objects.

The diagram below details how the Data Vault stores the datasets in the OCFL repository. Datasets are conceived as a
collection of Dataset Versions. Dataset versions are exported to Dataset Version Exports (DVEs). Currently, this is 
done as an RDA compliant bag. In the future other packaging formats may be supported.

![vault-impl](./vault-impl.png){:width="75%"}

Since every Dataset Version is stored in a separated OCFL object, multiple DVEs can be stored for the same Dataset
Version. This is necessary to support the following scenarios:

* Replacing a version that was updated in place, i.e. with "updatecurrent" in Dataverse. 
* Repackaging dataset versions in a different packaging format. 

[OCFL]: {{ ocfl_url }}