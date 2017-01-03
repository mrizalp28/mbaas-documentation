Uploading assets
----------------
With Nobackend, you can store and retrieve files and assets that hold data objects such as images, video, and audio content.

Nobackend manages these objects as Asset entities. Optionally, you can use Folder entities to organize related assets.

Uploading assets
~~~~~~~~~~~~~~~~
Assets can be any file type and can be attached to any entity. When an asset is uploaded, Nobackend will automatically detect the file metadata for the asset and save it in the associated entity as a ``file-metadata`` property. Only 1 asset can be attached to an entity.

To attach an asset to an entity, do the following:

Request syntax
^^^^^^^^^^^^^^

.. code::

    curl -X POST -F name='<filename>' -F file=@<file_location> 'https://api.tbaas.co/<org>/<app>/<collection>/<entity>

Parameters

================ ============================================================================= 
Parameter	     Description
================ =============================================================================
Filename         A filename to associate with the asset.
file_location    The location of the asset to be uploaded.
Org organization UUID or organization name
App application  UUID or application name
Collection       Name or UUID of the collection of the entity you want to attach the asset to.
Entity           Name or UUID of an existing entity you want to attach the asset to.
================ =============================================================================

Example request
^^^^^^^^^^^^^^^

.. code::

    curl -X POST -i -F name='clouds' -F file=@happy_clouds.jpg 'https://api.tbaas.co/your-org/your-app/pictures/'
    
Example response
^^^^^^^^^^^^^^^^

Notice the ``file-metadata`` property in the response.

.. code::

    {
        "action" : "post",
        "application" : "f34f4222-a166-11e2-a7f7-02e81adcf3d0",
        "params" : { },
        "path" : "/users",
        "uri" : "https://api.tbaas.co/amuramoto/sandbox/pictures",
        "entities" : [ {
        "uuid" : "410b213a-b379-11e3-a0e5-9953085ea376",
        "type" : "user",
        "name" : "test",
        "created" : 1395681911491,
        "modified" : 1399069838919,
        "name" : "clouds",    
        "file" : "fobnszewobnioerabnoiawegbrn\n",
        "file-metadata" : {
          "content-type" : "image/jpeg",
          "etag" : "\"2e1db7299b0a667ed80e674a0ef9d653\"",
          "last-modified" : 1399070010115,
          "content-length" : 28,
          "checksum" : "2e1db7299b0a667ed80e674a0ef9d653"
        },
        "metadata" : {
          "connecting" : {        
            "likes" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/connecting/likes"
          },
          "path" : "/users/410b213a-b379-11e3-a0e5-9953085ea376",
          "sets" : {
            "rolenames" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/roles",
            "permissions" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/permissions"
          },
          "connections" : {
            "follows" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/follows"
          },
          "collections" : {
            "activities" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/activities",
            "devices" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/devices",
            "feed" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/feed",
            "groups" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/groups",
            "roles" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/roles",
            "following" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/following",
            "followers" : "/users/410b213a-b379-11e3-a0e5-9953085ea376/followers"
          }
        }
        } ],
        "timestamp" : 1399070009986,
        "duration" : 441,
        "organization" : "your-org",
        "applicationName" : "your-app"
    }

Updating assets
~~~~~~~~~~~~~~~
To update the data for an asset, perform the same request outlined above in 'Uploading assets' as a ``PUT`` request rather than a ``POST``.
