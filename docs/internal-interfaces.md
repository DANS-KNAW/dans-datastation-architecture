Overview
========

The Data Station architecture follows the [microservices architectural style]{:target=_blank} as far as possible. Dataverse is the only component that is not a
microservice. It is a monolith that is used as a black box.

The interfaces between the microservices fall into the following categories:

* RESTful HTTP interfaces. These interfaces are described in the documentation page of the microservice.
* Shared disk space. In the automated deposit pipeline deposits are passed from one microservice to the next by storing
  them in a shared disk space. The interchange format that is used by several microservices is the [Deposit Directory].

[microservices architectural style]: https://www.martinfowler.com/microservices/

[Deposit Directory]: ./deposit-directory.md
