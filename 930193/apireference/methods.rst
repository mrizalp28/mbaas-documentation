Methods
-------
Access-Tokens
~~~~~~~~~~~~~

.. code:: 

    POST /management/token

Login with Admin-User or Organization credentials.

Parameters

* **login-credentials** ([LoginCredentials](#logincredentials))

Login credentials either username/password or id/secret. (Specified in body).

Responses

**200**

* Description: Object containing access_token.
* Schema: [AccessTokenResponse](#accesstokenresponse)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)

.. code::     

    POST /{orgId}/{appId}/token


Login with App-User or Application credentials.

Parameters

* **login-credentials** ([LoginCredentials](#logincredentials))

Login credentials either username/password or id/secret. (Specified in body).

Responses

**200**

* Description: Object containing access_token.
* Schema: [AccessTokenResponse](#accesstokenresponse)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    

Activities
~~~~~~~~~~

.. code:: 

    GET /{orgId}/{appId}/groups/{groupId}/feed

    GET a group's feed through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **groupId** (string)
One of the group's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of group's activity.
* Schema: [ActivityFeed](#activityfeed)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
  
.. code:: 

    POST /{orgId}/{appId}/users/{userId}/activities

Create an activity in the activities collection.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).
* **CreateActivity** ([CreateActivity](#createactivity))
One or more sets of activity properties. (Specified in body).

Responses

**200**

* Description: An array of user's activity.
* Schema: [ActivityFeed](#activityfeed)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)

.. code:: 

    GET /{orgId}/{appId}/users/{userId}/feed

Retrieve a user's feed through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).

Responses

**200**

* Description: An array of user's activity feed.
* Schema: [ActivityFeed](#activityfeed)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    

Admin-Users
~~~~~~~~~~~

.. code:: 

    GET /management/orgs/{orgId}/users

Retrieve details about the admin users in an organization.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved Admin user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /management/orgs/{orgId}/users/{userId}

Remove an admin user from an organization through providing both Id of application and organization.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **userId-2** (string)
One of the user's identification which includes username, email address or UUID. (Specified in path).

Responses

**200**

* Description: An array of     DELETEd Admin user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)

.. code::    

    POST /management/users

Create a whole new admin user.

Parameters

* **CreateAdminUser** ([CreateAdminUser](#createadminuser))
User entity with fields required for User creation. (Specified in body).

Responses

**200**

* Description: An API Response with a entities array containing the newly created Admin User.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/users/resetpw

Initiate the reset of an admin user's password.

Parameters

Responses

**200**

* Description: An array of complete messages.
* Schema: [Action](#action)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /management/users/resetpw

Complete the password reset through     GETting the newpassword and the old one for identification.

Parameters

* **ResetPWMsg** ([ResetPWMsg](#resetpwmsg))
Parameters and value for the Captcha challenge, the admin user's response to the Captcha challenge, and the admin user's email address. (Specified in body).

Responses

**200**

* Description: An array of complete messages.
* Schema: [](#)
    
**default**

* Description: 
* Schema: [Error](#error)
    
.. code::

    GET /management/users/{userId}

Retrieve details about an admin user.

Parameters

* **userId** (string)
One of the user's identification which includes username, real name, email address or UUID. (Specified in path).

Responses

**200**

* Description: An API Response with a entities array containing the Admin User.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    PUT /management/users/{userId}

Update the info of an admin user.

Parameters

* **userId** (string)
One of the user's identification which includes username, real name, email address or UUID. (Specified in path).

Responses

**200**

* Description: An API Response with a entities array containing the updated Admin User
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/users/{userId}/activate


Activate an admin user from a link provIded in an email notification.

Parameters

* **userId** (string)
One of the user's identification which includes username, real name, email address or UUID. (Specified in path).
* **token** (string)
Activation token's query statement. (Specified in query).
* **confirm_email** (boolean)
Query statement of whether send confimation email or not. (Specified in query).

Responses

**200**

* Description: An array of complete messages.
* Schema: [Action](#action)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    PUT /management/users/{userId}/password

Update an admin user's password through     GETting the newpassword and the old one for identification.

Parameters

* **userId** (string)
One of the user's identification which includes username, real name, email address or UUID. (Specified in path).
* **ResetPW** ([ResetPW](#resetpw))
The user's old and new password. (Specified in body).

Responses

**200**

* Description: An array of complete messages.
* Schema: [Action](#action)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/users/{userId}/reactivate

Reactivate an expired admin user.

Parameters

* **userId** (string)
One of the user's identification which includes username, real name, email address or UUID. (Specified in path).

Responses

**200**

* Description: An array of complete messages.
* Schema: [Action](#action)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    

App-Users
~~~~~~~~~

.. code::

    GET /{orgId}/{appId}/users


Retrieve users though query statement.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **queryStatement** (string)
The query statement of the User. (Specified in query).

Responses

**200**

* Description: An array of retrieved user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{appId}/users

Create a user in the users collection through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **CreateUser** ([CreateUser](#createuser))
The properties of the user. (Specified in body).

Responses

**200**

* Description: An array of created user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{appId}/users/{userId}

Retrieve a user through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **userId-2** (string)
One of the user's identification which includes username, email address or UUID. (Specified in path).

Responses

**200**

* Description: An array of retrieved user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    PUT /{orgId}/{appId}/users/{userId}

Update a user through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).

Responses

**200**

* Description: An array of updated user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /{orgId}/{appId}/users/{userId}

Remove a user through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).

Responses

**200**

* Description: An array of     DELETEd user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{appId}/users/{user}/password

Set a user's password or reset the user's existing password.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **username** (string)
The username of the user. (Specified in path).
* **ResetPW** ([ResetPW](#resetpw))
The user's old and new password. (Specified in body).

Responses

**200**

* Description: An array of complete messages.
* Schema: [Action](#action)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
Entities-Collections
~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /{orgId}/{appId}/users/{userId}/{relation}

Retrieve a user's collections or connections through query statement.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).
* **relation** (string)
The relation between user and collections. (Specified in path).
* **queryStatement** (string)
The query statement of the user. (Specified in query).

Responses

**200**

* Description: An array of user's collections info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{appId}/{collectionId}

Retrieve collection through query statement.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **collectionId** (string)
One of the collection's identification which includes name or uuid. (Specified in path).
* **queryStatement** (string)
Any values specified in the query statement should be enclosed in single-quotes. (Specified in query).

Responses

**200**

* Description: An array of retrieved collection's info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    PUT /{orgId}/{appId}/{collectionId}

Update collection through query statement.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **collectionId** (string)
One of the collection's identification which includes name or uuid. (Specified in path).
* **queryStatement** (string)
Any values specified in the query statement should be enclosed in single-quotes. (Specified in query).

Responses

**200**

* Description: An array of updated collection's info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{appId}/{collectionId}/{entityId1}/{relation}/{entityId2}

Add an entity to a collection through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **collectionId** (string)
One of the collection's identification which includes name or uuid. (Specified in path).
* **entityId1** (string)
The Id of the 1st entity. (Specified in path).
* **relation** (string)
The relation between 1st entity and 2nd entity. (Specified in path).
* **entityId2** (string)
The Id of the 2nd entity. (Specified in path).

Responses

**200**

* Description: An array of added entity's info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /{orgId}/{appId}/{collectionId}/{entityId1}/{relation}/{entityId2}

Remove an entity from a collection through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **collectionId** (string)
One of the collection's identification which includes name or uuid. (Specified in path).
* **entityId1** (string)
The Id of the 1st entity. (Specified in path).
* **relation** (string)
The relation between 1st entity and 2nd entity. (Specified in path).
* **entityId2** (string)
The Id of the 2nd entity. (Specified in path).

Responses

**200**

* Description: An array of     DELETEd entity's info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{appId}/{collectionId}/{entityId}

Retrieve an entity through providing Id of application, organization, collection and entity.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **collectionId** (string)
One of the collection's identification which includes name or uuid. (Specified in path).
* **entityId** (string)
One of the entity's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved entity's info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    PUT /{orgId}/{appId}/{collectionId}/{entityId}

One or more properties can be updated with a single request.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **collectionId** (string)
One of the collection's identification which includes name or uuid. (Specified in path).
* **entityId** (string)
One of the entity's identification which includes name or uuid. (Specified in path).
* **entityproperty** ([CreateEntities](#createentities))
The properties of the entity. (Specified in body).

Responses

**200**

* Description: An array of updated entity's info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /{orgId}/{appId}/{collectionId}/{entityId}

    DELETE an entity from the collection.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **collectionId** (string)
One of the collection's identification which includes name or uuid. (Specified in path).
* **entityId** (string)
One of the entity's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of     DELETEd entity's info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{appId}/{entitytype}

When a new entity is created, Nobackend will automatically create a corresponding collection if one does not already exist. The collection will automatically be named with the plural form of the entity type.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **entitytype** (string)
The entity type to create. (Specified in path).
* **entityproperty** ([CreateEntities](#createentities))
The properties of the entity. (Specified in body).

Responses

**200**

* Description: An array of created custom entity's info.
* Schema: [Entity](#entity)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    

Events
~~~~~~

.. code::

    POST /{orgId}/{appId}/events

Create an event through providing both Id of organization and application.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **CreateEvent** ([CreateEvent](#createevent))
The required property of the event. (Specified in body).

Responses

**200**

* Description: An array of created event's info.
* Schema: [Event](#event)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    

Groups
~~~~~~

.. code::

    POST /{orgId}/{appId}/groups

Create a new group through providing both Id of organization and application.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **groupproperty** ([CreateGroup](#creategroup))
The property of the created group. (Specified in body).

Responses

**200**

* Description: An array of created group's info.
* Schema: [Group](#group)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{appId}/groups/{groupId}/activities

Create an activity to a specific group. In this case the activity is created in the activities collection and is accessible at the /activities endpoint to users who have the permission to read that endpoint. In addition, a relationship is established between the activity and the group, and because of that, the activity will appear in the group’s feed. The group 'owns' the activity. Also, the activity will be published in the feed of all users that are members of the group.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **groupId** (string)
One of the group's identification which includes name or uuid. (Specified in path).
* **CreateActivity** ([CreateActivity](#createactivity))
One or more sets of activity properties. (Specified in body).

Responses

**200**

* Description: 
* Schema: [ActivityFeed](#activityfeed)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{appId}/groups/{groupId}/users/{userId}

Add a user to a group through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **groupId** (string)
One of the group's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).

Responses

**200**

* Description: An array of added user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /{orgId}/{appId}/groups/{groupId}/users/{userId}

    DELETE user from a group through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **groupId** (string)
One of the group's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).

Responses

**200**

* Description: An array of     DELETEd user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{org_Id}/{app_Id}/groups/{groupId}

    GET a group through through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **groupId** (string)
One of the group's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved group's info.
* Schema: [Group](#group)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    PUT /{org_Id}/{app_Id}/groups/{groupId}

Update a group through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **groupId** (string)
One of the group's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of updated group's info.
* Schema: [Group](#group)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    

Notifications
~~~~~~~~~~~~~

.. code::

    POST /{orgId}/{applicationId}/devices

Create notifications for user through tar    GETing by location and providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **notification** ([CreateNotifications](#createnotifications))
These Parameters are used when forming the notification portion of the request. (Specified in body).
* **queryStatement** (string)
The query statement of the location of the user. (Specified in query).

Responses

**200**

* Description: An array of created notification's info.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{applicationId}/devices/*/notifications

Create notifications for all devices. This request will tar    GET all device entities.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **notification** ([CreateNotifications](#createnotifications))
These Parameters are used when forming the notification portion of the request. (Specified in body).

Responses

**200**

* Description: An array of created notification's info.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{applicationId}/devices/{deviceId}/notifications

Create notifications for a single device. This request will tar    GET a specific device entity.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **deviceId** (string)
One of the device's identification which includes name or uuid. (Specified in path).
* **notification** ([CreateNotifications](#createnotifications))
These Parameters are used when forming the notification portion of the request. (Specified in body).

Responses

**200**

* Description: An array of created notification's info.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{applicationId}/groups/{path}/notifications

Create notifications for a group. This request will tar    GET all users associated with a specific group entity.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **path** (string)
The path of the group. (Specified in path).
* **notification** ([CreateNotifications](#createnotifications))
These Parameters are used when forming the notification portion of the request. (Specified in body).

Responses

**200**

* Description: An array of created notification's info.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{applicationId}/notifications

Retrieve one or more notifications through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).

Responses

**200**

* Description: An array of retrieved notification's info.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    PUT /{orgId}/{applicationId}/notifications/{notificationId}

Update a Notification in order to cancel the notifcation or set a new expiration time.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **notificationId** (string)
One of the notification's identification which includes name or uuid. (Specified in path).
* **notificationUpdate** ([NotificationUpdate](#notificationupdate))
Object with Notification fields to be updated. (Specified in body).

Responses

**200**

* Description: An API Response object containing an entity of type Notification.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /{orgId}/{applicationId}/notifications/{notificationId}

    DELETE an unsent Notification from the system.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **notificationId** (string)
One of the notification's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: API Response containing Notification entity that was     DELETEd.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{applicationId}/receipts

Retrieve one or more receipts through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).

Responses

**200**

* Description: An array of retrieved receipt's info.
* Schema: [Receipt](#receipt)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{applicationId}/users/{userId}/notifications

Create notifications for a user. This request will tar    GET a specific user entity.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).
* **notification** ([CreateNotifications](#createnotifications))
These Parameters are used when forming the notification portion of the request. (Specified in body).

Responses

**200**

* Description: An array of created notification's info.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{applicationId}/{deviceId}/*/receipts

Retrieve receipts associated with one or more devices through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **deviceId** (string)
One of the device's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved receipt's info.
* Schema: [Receipt](#receipt)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{applicationId}/{notificationId}/*/queue

Retrieve the list of devices associated with one or more notifications before the notifications are sent through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **notificationId** (string)
One of the notification's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved device's info.
* Schema: [Device](#device)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{applicationId}/{notificationId}/*/receipts

Retrieve receipts for one or more notifications through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **notificationId** (string)
One of the notification's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved receipt's info.
* Schema: [Receipt](#receipt)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{applicationId}/{receiptId}/*/notifications

Retrieve notifications associated with one or more receipts through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **applicationId** (string)
One of the application's identification which includes name or uuid (same as appId). (Specified in path).
* **receiptId** (string)
One of the receipt's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved notification's info.
* Schema: [Notification](#notification)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    

Organizations-Applications
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /management/orgs

Create an organization through a form     POST.

Parameters

* **CreateOrg** ([CreateOrg](#createorg))
A set of organization properties supplied through a form. (Specified in body).

Responses

**200**

* Description: An array of created Organization.
* Schema: [Organization](#organization)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/orgs/{orgId}

Retrieve an organization given a specified UUID or username.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of created Organization.
* Schema: [Organization](#organization)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/orgs/{orgId}/activate

Activate an organization from a link provIded in an email notification.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **token** (string)
Activation token. (Specified in query).
* **confirm_email** (boolean)
Send confirmation email or not. (Specified in query).

Responses

**200**

* Description: An array of complete messages.
* Schema: [Action](#action)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/orgs/{orgId}/apps

Retrieve the applications in an organization through providing both Id of application and organization.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved application data.
* Schema: [AppData](#appdata)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /management/orgs/{orgId}/apps/{appId}

Remove an application from an organization through providing both Id of application and organization.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of     DELETEd application info.
* Schema: [AppData](#appdata)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/orgs/{orgId}/apps/{appId}/credentials

Retrieve the client Id and client secret credentials for an application in an organization.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved credentials info.
* Schema: [Credential](#credential)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /management/orgs/{orgId}/apps/{appId}/credentials

Generate the client Id and client secret credentials for an application in an organization.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of generated credentials info.
* Schema: [Credential](#credential)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/orgs/{orgId}/credentials

Retrieve the credentials for an organization client.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of Credential
* Schema: [Credential](#credential)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /management/orgs/{orgId}/credentials

Generate whole new credentials for an organization client.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of Credential
* Schema: [Credential](#credential)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/orgs/{orgId}/feed

Retrieve an organization's activity feed.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of the organization's ActivityFeed.
* Schema: [ActivityFeed](#activityfeed)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/orgs/{orgId}/reactivate

Reactivate an expired organization.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of complete messages.
* Schema: [Action](#action)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /management/users/{userId}/feed

Retrieve an admin user's activity feed.

Parameters

* **userId** (string)
One of the user's identification which includes username, real name, email address or UUID. (Specified in path).

Responses

**200**

* Description: An array of user's activity
* Schema: [ActivityFeed](#activityfeed)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    

Permissions-Roles
~~~~~~~~~~~~~~~~~

.. code::

    GET /{orgId}/{appId}/roles

Retrieve the roles in an application through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An array of retrieved role's info.
* Schema: [Role](#role)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{appId}/roles

Create a new role through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **roleproperty** ([AddRole](#addrole))
The required properties of the role. (Specified in body).

Responses

**200**

* Description: An array of created role's info.
* Schema: [Role](#role)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /{orgId}/{appId}/roles/{roleId}/permissions

Remove permissions from a role.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **roleId** (string)
One of the role's identification which includes name or uuid. (Specified in path).
* **Permissions** ([Permissions](#permissions))
The query statement of the url pattern. (Specified in body).

Responses

**200**

* Description: Permissions object with array of the deleated Usergrid Permission strings.
* Schema: [Permissions](#permissions)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{appId}/roles/{roleId}/users

Retrieve the users in a role through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **roleId** (string)
One of the role's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: An API Response with a entities array of Users.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{appId}/roles/{roleId}/users/{userId}

Add a user to a role through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **roleId** (string)
One of the role's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).

Responses

**200**

* Description: An array of added user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /{orgId}/{appId}/roles/{roleId}/users/{userId}

Remove a user from a role through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **roleId** (string)
One of the role's identification which includes name or uuid. (Specified in path).
* **userId-3** (string)
One of the user's identification which includes username or UUID. (Specified in path).

Responses

**200**

* Description: An array of     DELETEd user's info.
* Schema: [User](#user)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    DELETE /{orgId}/{appId}/roles/{rolename}

Remove a role through providing all the identifications.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **rolename** (string)
The name of the role. (Specified in path).

Responses

**200**

* Description: An array of     DELETEd role's info.
* Schema: [Role](#role)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    GET /{orgId}/{applicationId}/roles/{roleId}/permissions

Retrieve permissions for a Role.

Parameters

* **orgId** (string)
One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **roleId** (string)
One of the role's identification which includes name or uuid. (Specified in path).

Responses

**200**

* Description: Permissions object with array of Usergrid Permission strings.
* Schema: [Permissions](#permissions)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
    
.. code::

    POST /{orgId}/{applicationId}/roles/{roleId}/permissions

Add permissions to a role through providing all the identifications.

Parameters

* **orgId** (string)

One of the organization's identification which includes name or uuid. (Specified in path).
* **appId** (string)
One of the application's identification which includes name or uuid. (Specified in path).
* **roleId** (string)
One of the role's identification which includes name or uuid. (Specified in path).
* **Permissions** ([Permissions](#permissions))
Permissions object with array of Usergrid Permission strings to be added. (Specified in body).

Responses

**200**

* Description: Permissions object with array of Usergrid Permission strings.
* Schema: [Permission](#permission)
    
**default**

* Description: Unexpected error.
* Schema: [Error](#error)
