Development
===========
The following sections discuss development on various parts of a Data Station. Some components are being developed by DANS, other components are provided by
open source projects in which DANS may participate.

DANS microservices
------------------
The DANS microservices are based on the [dans-module-archetype]{:target=_blank}. This archetype creates a skeleton microservice based on the
[DropWizard]{:target=_blank} framework. When working on DANS microservices, please comply with the [common practises](dev-common-practices.md).

DANS command-line tools
-----------------------
DANS command line tools are written in Java as well. They are based on the [dans-cli-archetype]{:target=_blank}. This archetype creates a skeleton command line
tool which uses some of the DropWizard facilities.

DANS APIs
---------
Most of the [DANS microservices](#dans-microservices) implement an API. The API is specified in an OpenAPI document which is packaged as an artifact by a
separated module. The microservice and command-line tool use this artifact to generate the server and client proxies respectively. If a microservice calls
another DANS microservice, it will use that other microservice's API module to generate a client proxy as well.

There is an archetype to create API modules called [dans-api-archetype]{:target=_blank}.

!!! note "Project names"

    * Microservices, command-line tools and APIs have name starting with `dd-`.
    * Command-line tools base their name on the microservice they call, adding the suffix `-cli`, e.g., `dd-data-vault-cli`.
    * API modules also base their name on the microservice they belong to, adding the suffix `-api`, e.g., `dd-data-vault-api`.
    * Libraries, plugins and profiles have names starting with `dans-`, e.g., `dans-bagit-profile`.

Dataverse
---------
The [architecture overview](index.md) makes clear that Dataverse plays a key role in the Data Station. That is why DANS
is actively involved in its development via the Dataverse community. When working on Dataverse code, take notice of
the [developer docs]{:target=_blank}.

!!! note "Debugging Dataverse"

    For DANS developers it is **not necessary (nor preferable)** to set up Dataverse and its dependencies Solr and 
    PostGreSQL on your development laptop, as described in the developer docs. Instead you should use the pre-built 
    vagrant boxes, which are available only for DANS developers. 

Skosmos
-------
[Skosmos]{:target=_blank} is used to serve vocabulary terms to Dataverse. DANS is currently not actively involved in
development, but it is entirely possible that bug fixes may need to be contributed in the future. The project is written
in PHP, but there is no information on the Skosmos website about the development environment set-up.

Documentation with mkdocs
-------------------------
The documentation for DANS projects (including this site) is written using [mkdocs]{:target=_blank}. The source code for
those sites consists of Markdown in combination with other resources, such as images. Images are often created
with [yEd]{:target=_blank}. The graphml source code of the images is committed along with the image exports. You should
always check that your changes render correctly. This is made easy by the `start-mkdocs.sh` script
in [dans-dev-scripts]{:target=_blank}.

Local testing
-------------
The [dans-dev-scripts]{:target=_blank} can also be used to run microservices and command-line tools from their project directory.
See the README.md in the project for more information.

[dans-api-archetype]: https://dans-knaw.github.io/dans-api-archetype/

[dans-module-archetype]: https://dans-knaw.github.io/dans-smodule-archetype/

[dans-cli-archetype]: https://dans-knaw.github.io/dans-cli-archetype/

[DropWizard]: https://www.dropwizard.io/en/latest/

[best practises]: https://dans-knaw.github.io/dans-module-archetype/common-practices/

[Poetry]: https://python-poetry.org/docs/

[DANS-KNAW PyPI account]: https://pypi.org/user/DANS-KNAW/

[PyCharm]: https://www.jetbrains.com/pycharm/

[developer docs]: https://guides.dataverse.org/en/latest/developers/index.html

[mkdocs]: https://www.mkdocs.org/

[yEd]: https://www.yworks.com/products/yed

[dans-dev-scripts]: https://github.com/DANS-KNAW/dans-dev-scripts

[Skosmos]: {{ skosmos_url }}

