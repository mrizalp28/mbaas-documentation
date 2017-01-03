Social Graph Connections
------------------------
One of the most useful features of Nobackend is the ability to create connections between entities, which allow you to model arbitrary relationships between entities. This feature is particularly powerful when applied to user entities by allowing you to model complex social graphs between users as well as groups of users.

Following/followers
~~~~~~~~~~~~~~~~~~~
To make the social graph possibilities of entity connections even easier to achieve, Nobackend also has special support for a default following/followers relationship, which offers these additional features:

Reciprocal connection: If a following connection is made between a user and another user, a reciprocal followers relationship will be created automatically. In contrast, all of other entity connections are one-way, meaning any reciprocal relationship must be created manually.

Activity feed subscription: The followed user's activities will automatically be posted to the following user's activity feed. For example, if Arthur is following Ford, then any activities published by Ford that Arthur is allowed to see will appear in Arthur's activity feed.

Creating a following/followers connection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
To create a following/followers connection between two entities, create the connection as you would any generic entity connection. For full details on creating connections, see [Connecting entities](../entity-connections/connecting-entities.html). 

For example, the following request would create a following/followers relationship between two user entities with the usernames 'Fred' and 'Barney'::

    POST https://api.tbaas.co/your-org/your-app/users/barney/following/users/fred

.. Note:: Please note that this only works when you ``POST`` a ``following`` connection. Creating a follower connection would not create a reciprocal following connection.

This would retrieve a list of the users that Barney is following::

    GET https://api.tbaas.co/your-org/your-app/users/barney/following
    
And this would retrieve a list of users that are following Fred::

    GET https://api.tbaas.co/your-org/your-app/users/fred/followers
    
