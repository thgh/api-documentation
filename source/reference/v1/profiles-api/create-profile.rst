.. _v1/profiles-create:

Profiles API v1: Create profile
===============================
``POST`` ``https://api.mollie.com/v1/profiles``

Authentication: :ref:`OAuth access tokens <oauth/overview>`

In order to process payments, you need to create a website profile. A website profile can easily be created via the
Dashboard manually. However, the Mollie API also allows automatic profile creation via the Profiles API.

A profile's API keys can be set up with this API as well.

Parameters
----------
.. list-table::
   :widths: auto

   * - | ``name``
       | string
     - The profile's name should reflect the tradename or brand name of the profile's website or application.

   * - | ``website``
       | string
     - The URL to the profile's website or application. The URL should start with ``https://`` or ``http://``.

   * - | ``email``
       | string
     - The email address associated with the profile's tradename or brand.

   * - | ``phone``
       | string
     - The phone number associated with the profile's tradename or brand.

   * - | ``categoryCode``
       | integer
     - The industry associated with the profile's tradename or brand.

       Possible values:

       * ``5399`` General merchandise
       * ``5732`` Electronics, computers, and software
       * ``4121`` Travel, rental, and transportation
       * ``6012`` Financial services
       * ``5499`` Food and drinks
       * ``7999`` Events, festivals, and recreation
       * ``5192`` Books, magazines, and newspapers
       * ``7299`` Personal services
       * ``8398`` Charity and donations
       * ``0`` Other

   * - | ``mode``
       | string
     - Optional – Creating a test profile by setting this parameter to ``test``, enables you to start using the API
       without having to provide all your business info just yet. Defaults to ``live``.

       Possible values: ``live`` ``test``

Response
--------
``201`` ``application/json; charset=utf-8``

A profile object is returned, as described in :ref:`Get profile <v1/profiles-get>`.

Example
-------

Request
^^^^^^^
.. code-block:: bash

   curl -X POST https://api.mollie.com/v1/profiles \
       -H "Authorization: Bearer access_Wwvu7egPcJLLJ9Kb7J632x8wJ2zMeJ" \
       -d "name=My website name" \
       -d "website=https://www.mywebsite.com" \
       -d "email=info@mywebsite.com" \
       -d "phone=31123456789" \
       -d "categoryCode=5399" \
       -d "mode=live"

Response
^^^^^^^^
.. code-block:: http

   HTTP/1.1 201 Created
   Content-Type: application/json; charset=utf-8

   {
       "resource": "profile",
       "id": "pfl_v9hTwCvYqw",
       "mode": "live",
       "name": "My website name",
       "website": "https://www.mywebsite.com",
       "email": "info@mywebsite.com",
       "phone": "31123456789",
       "categoryCode": 5399,
       "status": "unverified",
       "review": {
           "status": "pending"
       },
       "createdDatetime": "2018-03-17T00:22:06.0Z",
       "updatedDatetime": "2018-03-17T00:22:06.0Z",
       "links": {
           "apikeys": "https://api.mollie.com/v1/profiles/pfl_v9hTwCvYqw/apikeys"
       }
   }