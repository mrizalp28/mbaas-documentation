Revoking tokens (logout)
------------------------
Under certain circumstances, you may need to explicitly revoke one or more tokens associated with a user entity, such as when a user logs out of your app. This is accomplished by making a PUT request to the /revoketoken and /revoketokens endpoints.

Revoking tokens (user logout)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
If a user has been logged in using the Usergrid iOS, Android, JavaScript or node.JS SDKs, the returned token is automatically stored in the NobackendDataClient (iOS), DataClient (Android), Nobackend.Client (JavaScript), Nobackend.Client (node.JS) class instance. Calling the logout method of the SDK will destroy the token on the server, as well as in the client object.

Request syntax
^^^^^^^^^^^^^^
Revoke all tokens associated with a user entity

.. code::

    curl -X PUT https://api.tbaas.co/<org_name>/<app_name>/users/<user_uuid_or_username>/revoketokens
		
Revoke a specific token associated with a user entity

.. code::

    curl -X PUT https://api.tbaas.co/<org_name>/<app_name>/users/<user_uuid_or_username>/revoketoken?token=<token_to_revoke>			
		
Example request
^^^^^^^^^^^^^^^

.. code::

    curl -X PUT https://api.tbaas.co/your-org/your-app/users/someUser/revoketokens
		
Example response

.. code::

    {
      "action" : "revoked user token",
      "timestamp" : 1382050891455,
      "duration" : 24
    }     

Revoking admin user tokens
^^^^^^^^^^^^^^^^^^^^^^^^^^
The /revoketoken and /revoketokens endpoints also work for revoking admin user tokens by making a PUT request to /management/users/<org_admin_username>/
