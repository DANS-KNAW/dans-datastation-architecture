Development
===========
The following sections discuss development on various parts of a Data Station. Some components are developed by DANS,
other components are provided by open source projects in which DANS may participate.

DANS microservices
------------------
The DANS microservices are based on the [dans-module-archetype]{:target=_blank}. This archetype creates a skeleton
microservice based on the [DropWizard]{:target=_blank} framework. When working on DANS microservices, please comply
with the [best practises]{:target=_blank} documented in the dans-module-archetype documentation.

DANS command-line tools
-----------------------
DANS command line tools are written in Java as well. They are based on the [dans-cli-archetype]{:target=_blank}. This archetype
creates a skeleton command line tool which uses some of the DropWizard facilities.

!!! note "Python command line tools"

    Previously DANS command line tools were written in Python, but his approach is being phased out.


Dataverse
---------
The [architecture overview](index.md) makes clear that Dataverse plays a key role in the Data Station. That is why DANS
is actively involved in its development via the Dataverse community. When working on Dataverse code, take notice of
the [developer docs]{:target=_blank}.

!!! note "Debugging Dataverse"

    For DANS developers it is **not necessary (nor preferable)** to set up Dataverse and its dependencies Solr and 
    PostGreSQL on your development laptop, as described in the developer docs. Instead you should use the pre-build 
    vagrant box, which is available only for DANS developers. 

Skosmos
-------
[Skosmos]{:target=_blank} is used to serve vocabulary terms to Dataverse. DANS is currently not actively involved in
development, but it is entirely possible that bug fixes may need to be contributed in the future. The project is written
in PHP but there is no information on the Skosmos website about the development environment set-up.

Documentation with mkdocs
-------------------------
The documentation for DANS projects (including this site) is written using [mkdocs]{:target=_blank}. The source code for
those sites consists of markdown in combination with other resources, such as images. Images are often created
with [yEd]{:target=_blank}. The graphml source code of the images is committed along with the image exports. You should
always check that your changes render correctly. This is made easy by the `start-mkdocs.sh` script
in the `dans-core-systems` project (only available for DANS developers).

[dans-module-archetype]: https://dans-knaw.github.io/dans-module-archetype/

[dans-cli-archetype]: https://dans-knaw.github.io/dans-cli-archetype/

[DropWizard]: https://www.dropwizard.io/en/latest/

[best practises]: https://dans-knaw.github.io/dans-module-archetype/common-practices/

[Poetry]: https://python-poetry.org/docs/

[DANS-KNAW PyPI account]: https://pypi.org/user/DANS-KNAW/

[PyCharm]: https://www.jetbrains.com/pycharm/

[developer docs]: https://guides.dataverse.org/en/latest/developers/index.html

[mkdocs]: https://www.mkdocs.org/

[yEd]: https://www.yworks.com/products/yed

[dans-dev-tools]: https://github.com/DANS-KNAW/dans-dev-tools#dans-dev-tools

[Skosmos]: {{ skosmos_url }}