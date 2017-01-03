Creating other connections
--------------------------
You can extend this connection structure to create connections using any relationship. For example, you could use likes to denote a connection between a user and his dog with this POST::

    POST https://api.tbaas.co/your-org/your-app/users/Fred/likes/dogs/Dino
    
Note that in this case a reciprocal connection is not automatically created. To do so you would need to manually create the reciprocal connection with another POST such as::

    POST https://api.tbaas.co/your-org/your-app/dogs/Dino/liked_by/users/Fred
    
For more information on using entity connections, see [Connecting entities](../entity-connections/connecting-entities.html).