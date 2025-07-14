About this site
===============

This documentation site discusses the technical details of the core software-based services of DANS, the Dutch national
centre of expertise and repository for research data. It is intended for developers and system administrators, both
within DANS and outside.

For more general information on DANS, its mission and services, see the [DANS website]{:target=_blank}.

The documentation discusses the following topics:

* _Architecture_. The core services of DANS are centered around the concept of a **Data Station**. See
  [Core Services](./core-services.md) for more information about what services are available.
  Each Data Station has basically the same structure. To read more about the architecture of a Data
  Station, see the section about the [Data Station architecture](./datastation.md). This page is also a jumping off
  point for more detailed information about the various components of the system.
* _Configurations_. The basic Data Station configuration has a couple of
  variations such as [DataverseNL](./dataversenl.md), [Vault as a Service](./vaas.md)
* _Interfaces_. The Data Stations have a number of interfaces, both internal and external. For more information, see
  the sections about [internal interfaces](./internal-interfaces.md) and
  about [external interfaces](./external-interfaces.md).
* _Migration_. The Data Stations are the successor of the legacy repository system [EASY]{:target=_blank}, which was in use from 2007 
  until 2024. Some parts of this documentation still contain references to EASY, but these will be removed as we 
  are wrapping up the migration process.
* _Development_. The Data Stations are developed by the DANS Core Systems Team. For more information about the
  development environment, see the section about [development](./dev.md).

[DANS website]: {{ dans_website }}
[EASY]: {{ easy }}