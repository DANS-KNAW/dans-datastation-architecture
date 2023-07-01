Overview
========

The Data Station architecture follows the [microservices architectural style]{:target=_blank} as far as components are
developed by DANS itself. The interfaces between the microservices fall into the following categories:

* RESTful HTTP interfaces. These interfaces are described in the documentation page of the microservice.
* Shared disk space. In the automated deposit pipeline deposits are passed from one microservice to the next by storing
  them in a shared disk space. The requirements for the deposit layout i

[microservices architectural style]: https://www.martinfowler.com/microservices/