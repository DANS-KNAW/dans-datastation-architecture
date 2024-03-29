Overview
========

The Data Station architecture follows the [microservices architectural style]{:target=_blank} as far as much as
possible. Dataverse is the only component that is not a microservice. It is a monolith that is used as a black box.

The interfaces between the microservices fall into the following categories:

* RESTful HTTP interfaces. These interfaces are described in the documentation page of the microservice.
* Shared disk space. In the automated deposit pipeline deposits are passed from one microservice to the next by storing
  them in a shared disk space. In this category fall the following interfaces:
    * [Deposit Directory](./deposit-directory.md)
    * [Data Vault](./data-vault)

[microservices architectural style]: https://www.martinfowler.com/microservices/