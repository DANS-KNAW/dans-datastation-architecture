SWORD
=====

The Simple Web-service Offering Repository Deposit (SWORD) protocol is a standard for depositing content into
repositories. The DANS implementation of **version 2** of this protocol has been operational for several years for
depositing datasets in [EASY](./migration.md). The SWORD2 interface is also available in the Data Stations.

!!! note "SWORD3 not yet available"

    The latest version of SWORD is version 3. This version is not yet available in the Data Stations. Currently, we are 
    focusing on guaranteeing the continued availability of the SWORD2 interface for our existing customers. It is not yet
    decided whether we will implement SWORD3 in the future. 

Guide and code examples for SWORD2 client developers
----------------------------------------------------
The following documents and examples are available for developers who want to use the DANS SWORD2 service:

* [Guide for DANS SWORD2 client developers]{:target=_blank}
* [Code examples]{:target=_blank}

DANS BagIt Profile
------------------
The bags that are deposited to the DANS SWORD2 service must comply with the DANS BagIt Profile.

* [DANS BagIt Profile v1]{:target=_blank}

[Guide for DANS SWORD2 client developers]: {{ sword2_examples_docs }}
[Code examples]: {{ sword2_examples }}
[DANS BagIt Profile v1]: {{ dans_bagit_profile }}
