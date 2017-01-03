Creating Notifier
-----------------
When you request that a push notification be sent to your app on devices, an Usergrid notifier carries the request to the notification service (Google GCM or Apple APNs).

A notifier is represented by an entity in your Nobackend application (see the [API Docs](../rest-endpoints/api-docs.html) for reference information). It carries the credentials that authorize your request. Once a notification service has verified that your notifier contains valid credentials, it will forward your push notification to your app on devices.

You can create a notifier in two ways: using the admin portal and programmatically.

.. Note:: For an overview of how to set up push notifications, including troubleshooting tips, see [Adding push notifications support](adding-push-support.html).

Requirements
~~~~~~~~~~~~
To create a notifier, you must first register your app with the appropriate notification service, as described in [Registering with a notification service](registration.html).

Creating notifiers with the admin portal
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
To create a notifier with the admin portal, do the following:

1. Log in to the admin portal.
2. In the left nav, select **Push > Configuration**.
3. Click the **Apple** or **Android** tab.
4. If you have not already done so, retrieve your .p12 certificate (iOS apps) or API key (Android apps) by following the steps in the [Registering with a notification service](registration.html).
5. In the admin portal's Configuration page, enter values for the platform on which your mobile app will be installed.

The fields are different depending on whether you are on the Apple or Android tab:

**Fields for Apple**

=====================   ===============================================================
Name this notifier	    Enter a unique name that can be used to identify this notifiers
=====================   ===============================================================
Certificate	            Click **Choose File** to select the .p12 certificate you generated and saved to your desktop earlier in this tutorial.
Environment             Select the environment appropriate to your app. You may select development or production. Note that for the environment you select, you should have a separate .p12 certificate -- different certificates for development and production.
Certificate Password	Enter a certificate password if one was specified when you created your .p12 certificate
=====================   ===============================================================

**Fields for Android**

=====================   ===============================================================
Name this notifier	    Enter a unique name that can be used to identify this notifiers
=====================   ===============================================================
API Key                 Enter the API key that was generated when you registered your app with GCM. To retrieve your API key, go to the [Google API developer web site](https://code.google.com/apis/console/), then select **APIs & Auth > Credentials**
=====================   ===============================================================

6. Click **Create Notifier**. The Nobackend will create a notifier entity in the /notifiers collection. The notifier will also appear in the list of notifiers in the notifications console.

Creating notifiers programmatically
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
You can create an App BaaS notifier programmatically by sending requests to the Nobackend API.

For Apple
^^^^^^^^^

.. code::

    curl -X POST -i -H "Accept: application/json" -H "Accept-Encoding: gzip, deflate" -H "Authorization: Bearer YWMtFeeWEMyNEeKtbNX3o4PU0QAAAT8vzK3xz3utVZat0CosiYm75C2qpiGT79c" -F "name=applenotifier" -F "provider=apple" -F "environment=development" -F "p12Certificate=@/Users/me/dev/pushtest_dev.p12" 'https://api.tbaas.co/my-org/my-app/notifiers'

For Google
^^^^^^^^^^

.. code::

    curl -X POST "https://api.tbaas.co/my-org/my-app/notifiers" -d '{"name":"androiddev", "provider":"google", "apiKey":"AIzaSyCkXOtBQ7A9GoJsSLqZlod_YjEfxxxxxxx"}'

Notifier endpoints
~~~~~~~~~~~~~~~~~~
The following are the available notifier endpoints. For details on notifier properties, see the [API Docs](../rest-endpoints/api-docs.html). 

Base URL: ``https://api.tbaas.co/my-org/my-app/``

Working with one or more notifiers::

    /notifiers
    
Working with notifiers associated with specific devices::

    /devices/{device-id}/notifier

