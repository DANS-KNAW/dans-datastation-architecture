External interfaces
===================

The following interfaces are exposed to the outside world:

* The user interface of Dataverse. See for more information the [Dataverse User Guide]{:target=_blank}.
* The RESTful HTTP API of Dataverse. See for more information the [Dataverse API Guide]{:target=_blank}.


* A SWORD2 deposit interface. See for more information the [SWORD](./sword.md) page.

!!! warn "Dataverse API partially disabled"

    The Dataverse API is currently partially disabled in the Data Stations as a workaround for a limitation in Dataverse.
    Specifically, it is currently not possible to guard certain metadata blocks against changes by users. However, for 
    the Data Stations is it crucial that the Vault Metadata added by the system can only be changed by the system.

    A future release of Dataverse will allow metadata blocks to be protected by a key. Until that time, API 
    endpoints that write metadata are disabled.

[Dataverse User Guide]: {{ dataverse_user_guide }}
[Dataverse API Guide]: {{ dataverse_api_guide }}