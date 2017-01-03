Creating & incrementing counters
--------------------------------
To create a new counter or increment an existing counter, include the counter property in the body of a POST to the /events endpoint. More than one counter can be incremented in the same request.

**Note**: It may take up to 30 seconds after an event has been posted for the counter to be incremented.

Request syntax
~~~~~~~~~~~~~~

.. code::

    curl -X POST https://api.tbaas.co/<org>/<app>/events -d '{"timestamp":<timestamp>, "counters" : {<counter_name>:<increment_value>}}'
    
Parameters

========================== =========================================
Resource                   Description
========================== =========================================
Org	Organization           UUID or organization name
App	Application            UUID or application name
Timestamp                  A required UNIX timestamp that specifies the time the counter is being incremented.
counter_name               The name of the counter to create or the existing counter to increment.
increment_value            The value to increment the counter by.
========================== =========================================

Regarding the ``increment_value``, a negative number can be specified to decrement the value. A value of '0' can be specified to reset the value of the counter.

For the ``timestamp``, specifying a value of 0 will automatically assign the current time.

Example request
~~~~~~~~~~~~~~~
The following request will increment the 'button_clicks' counter by one, with a timestamp of the current time.

.. code::

    curl -X POST https://api.tbaas.co/your-org/your-app/events -d '{"timestamp":0, "counters" : {"button_clicks":1}}'
    
Example response
~~~~~~~~~~~~~~~~

.. code::

    {
      "action" : "post",
      "application" : "f34f4222-a166-11e2-a7f7-02e81adcf3d0",
      "params" : { },
      "path" : "/events",
      "uri" : "https://api.tbaas.co/your-org/your-app/events",
      "entities" : [ {
        "uuid" : "b11217fc-9d3a-1427-b24e-699740088e05",
        "type" : "event",
        "created" : 1401224590293,
        "modified" : 1401224590293,
        "timestamp" : 1401224590293,
        "counters" : {
          "button_clicks" : 1
        },
        "message" : null,
        "metadata" : {
          "path" : "/events/b11217fc-9d3a-1427-b24e-699740088e05"
        }
      } ],
      "timestamp" : 1401224590291,
      "duration" : 30,
      "organization" : "your-org",
      "applicationName" : "your-app"
    }
		