Core Services Overview
======================

!!! note "Migration in progress"
    
    This documentation describes the future core services of DANS. As of writing, the services are still under
      

The DANS Core Services are centered around the concept of a **Data Station**. A Data Station is a repository system that
is used for depositing, storing and disseminating datasets, as well as creating long-term preservation copies of those
datasets. These long-term preservation copies are stored in the DANS Data Vault. The following diagram gives a
high-level overview:

![Context](context.png)

* Each Data Station targets a part of the scientific research community. There is a Data Station for each of:
     * [Archaeology]{:target=_blank}
     * [Social Sciences & Humanities]{:target=_blank} 
     * Life, Health & Medical Sciences 
     * Physical & Technical Sciences
* The Data Stations use [Dataverse]{:target=_blank} as their repository system. Dataverse is an open source
  repository system developed by Harvard University.
* The Data Stations create a long-term preservation copy of each dataset in the DANS Data Vault.

[Dataverse]: {{ dataverse_org }}
[Archaeology]: {{ ds_archaeology }}
[Social Sciences & Humanities]: {{ ds_ssh }}