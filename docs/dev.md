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
DANS command line tools are written in Python. [Poetry]{:target=_blank} is used as the build tool. The Python-based
modules are released to the [DANS-KNAW PyPI account]{:target=_blank}. [PyCharm]{:target=_blank} is the preferred IDE for
Python-based projects.

Dataverse
---------
The [architecture overview](index.md) makes clear that Dataverse plays a key role in the Data Station. That is why DANS
is actively involved in its developmentvia the Dataverse community. When working on Dataverse code take notice of
the [developer docs]{:target=_blank}.

!!! note "Debugging Dataverse"

    For DANS developers it is **not necessary (nor preferable)** to set up Dataverse and its dependencies Solr and 
    PostGreSQL on your development laptop, as described in the developer docs. Instead you should use the pre-build 
    vagrant box. Information can be found in the private repository 
    [dd-dtap](https://github.com/DANS-KNAW/dd-dtap/blob/master/docs/dataverse-dev-with-vagrant.md){:target=_blank} 
    (only accessible for DANS developers).

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
in [dans-dev-tools]{:target=_blank}.


[dans-module-archetype]: https://dans-knaw.github.io/dans-module-archetype/

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