
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-retrieve-of-list-flavors-flavors:

Retrieve of list flavors
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /flavors

Retrieves IDs, names, and links for all available flavors.

This operation lists information for all available flavors.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200 203                   |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Error                    |A general error has      |
|                          |                         |occured.                 |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |Unauthorized.            |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |Forbidden.               |
+--------------------------+-------------------------+-------------------------+
|405                       |Bad Method               |Bad method.              |
+--------------------------+-------------------------+-------------------------+
|409                       |Conflicting Reqest       |Conflicting request.     |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|500                       |API Fault                |API fault.               |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The requested service is |
|                          |                         |unavailable.             |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""






This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|minDisk                   |Int *(Optional)*         |Filters the list of      |
|                          |                         |flavors to those with    |
|                          |                         |the specified minimum    |
|                          |                         |number of gigabytes of   |
|                          |                         |disk storage.            |
+--------------------------+-------------------------+-------------------------+
|minRam                    |Int *(Optional)*         |Filters the list of      |
|                          |                         |flavors to those with    |
|                          |                         |the specified minimum    |
|                          |                         |amount of RAM in         |
|                          |                         |megabytes.               |
+--------------------------+-------------------------+-------------------------+
|marker                    |String *(Optional)*      |The ID of the last item  |
|                          |                         |in the previous list.    |
+--------------------------+-------------------------+-------------------------+
|limit                     |Int *(Optional)*         |Sets the page size.      |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




**Example Retrieve of list flavors: JSON request**


.. code::

   X-Auth-Token: f064c46a782c444cb4ba4b6434288f7c
   Content-Type: application/json
   Accept: application/json





Response
""""""""""""""""





This table shows the body parameters for the response:

+----------------------------+------------------------+------------------------+
|Name                        |Type                    |Description             |
+============================+========================+========================+
|parameters.\ **flavors**    |Array                   |The array of flavors.   |
+----------------------------+------------------------+------------------------+
|parameters.flavors.ID       |String                  |The flavor ID.          |
+----------------------------+------------------------+------------------------+
|parameters.flavors.\        |String                  |The array of flavor     |
|**links**                   |                        |links for self and      |
|                            |                        |bookmark.               |
+----------------------------+------------------------+------------------------+
|parameters.flavors.links.\  |Uuid                    |The URL for the flavor  |
|**href**                    |                        |and the associated      |
|                            |                        |``rel``.                |
+----------------------------+------------------------+------------------------+
|parameters.flavors.links.\  |Uuid                    |The descriptive field   |
|**rel**                     |                        |for the associated      |
|                            |                        |``href``, which is      |
|                            |                        |either ``self`` or      |
|                            |                        |``bookmark``.           |
+----------------------------+------------------------+------------------------+
|parameters.flavors.\        |String                  |The flavor name.        |
|**name**                    |                        |                        |
+----------------------------+------------------------+------------------------+







**Example Retrieve of list flavors: JSON response**


The following example shows only a few flavors in the list for brevity.

.. code::

       Status Code: 200 OK
       Content-Length: 9132
       Content-Type: application/json
       Date: Wed, 08 Jul 2015 21:33:49 GMT, Wed, 08 Jul 2015 21:33:49 GMT
       Server: Jetty(9.2.z-SNAPSHOT)
       Via: 1.1 Repose (Repose/6.2.1.2)
       X-Compute-Request-Id: req-dbb15502-9620-450b-a05e-63e291595a89


.. code::

   {
       "flavors": [
           {
               "id": "2",
               "links": [
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/v2/453265/flavors/2",
                       "rel": "self"
                   },
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/453265/flavors/2",
                       "rel": "bookmark"
                   }
               ],
               "name": "512MB Standard Instance"
           },
           {
               "id": "3",
               "links": [
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/v2/453265/flavors/3",
                       "rel": "self"
                   },
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/453265/flavors/3",
                       "rel": "bookmark"
                   }
               ],
               "name": "1GB Standard Instance"
           },
           {
               "id": "4",
               "links": [
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/v2/453265/flavors/4",
                       "rel": "self"
                   },
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/453265/flavors/4",
                       "rel": "bookmark"
                   }
               ],
               "name": "2GB Standard Instance"
           },
           {
               "id": "5",
               "links": [
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/v2/453265/flavors/5",
                       "rel": "self"
                   },
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/453265/flavors/5",
                       "rel": "bookmark"
                   }
               ],
               "name": "4GB Standard Instance"
           },
           {
               "id": "6",
               "links": [
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/v2/453265/flavors/6",
                       "rel": "self"
                   },
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/453265/flavors/6",
                       "rel": "bookmark"
                   }
               ],
               "name": "8GB Standard Instance"
           },
           {
               "id": "7",
               "links": [
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/v2/453265/flavors/7",
                       "rel": "self"
                   },
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/453265/flavors/7",
                       "rel": "bookmark"
                   }
               ],
               "name": "15GB Standard Instance"
           },
           {
               "id": "8",
               "links": [
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/v2/453265/flavors/8",
                       "rel": "self"
                   },
                   {
                       "href": "https://dfw.servers.api.rackspacecloud.com/453265/flavors/8",
                       "rel": "bookmark"
                   }
               ],
               "name": "30GB Standard Instance"
   
           
           }
       ]
   }




