
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-retrieve-list-of-virtual-interfaces-servers-server-id-os-virtual-interfacesv2:

Retrieve list of virtual interfaces
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /servers/{server_id}/os-virtual-interfacesv2

Retrieves list of the virtual interfaces configured for a server instance.

This operation lists the virtual interfaces configured for a server instance.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{server_id}               |Uuid                     |The UUID for the server. |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""





This table shows the body parameters for the response:

+----------------------------------------------+--------------+----------------+
|Name                                          |Type          |Description     |
+==============================================+==============+================+
|parameters.\ **virtual_interfaces**           |Array         |The array of    |
|                                              |              |virtual         |
|                                              |              |interfaces.     |
+----------------------------------------------+--------------+----------------+
|parameters.virtual_interfaces.\ **id**        |String        |The virtual     |
|                                              |              |interface ID.   |
+----------------------------------------------+--------------+----------------+
|parameters.virtual_interfaces.\               |Array         |The array of    |
|**ip_addresses**                              |              |interface IP    |
|                                              |              |address details.|
+----------------------------------------------+--------------+----------------+
|parameters.virtual_interfaces.ip\             |String        |The interface   |
|**addresses**.\ **address**                   |              |IP address.     |
+----------------------------------------------+--------------+----------------+
|parameters.virtual_interfaces.ip_addresses.\  |Uuid          |The interface   |
|**network_id**                                |              |network ID.     |
+----------------------------------------------+--------------+----------------+
|parameters.virtual_interfaces.ip_addresses.\  |String        |The interface   |
|**network_label**                             |              |network label.  |
+----------------------------------------------+--------------+----------------+
|parameters.virtual_interfaces.\               |String        |The Media       |
|**mac_address**                               |              |Access Control  |
|                                              |              |(MAC) address   |
|                                              |              |for the virtual |
|                                              |              |interface. A    |
|                                              |              |MAC address is  |
|                                              |              |a unique        |
|                                              |              |identifier      |
|                                              |              |assigned to     |
|                                              |              |network         |
|                                              |              |interfaces for  |
|                                              |              |communications  |
|                                              |              |on the physical |
|                                              |              |network segment.|
+----------------------------------------------+--------------+----------------+







**Example Retrieve list of virtual interfaces: JSON response**


.. code::

       Status Code: 200 OK
       Content-Length: 585
       Content-Type: application/json
       Date: Wed, 08 Apr 2015 14:24:10 GMT, Wed, 08 Apr 2015 14:24:11 GMT
       Server: Jetty(9.2.z-SNAPSHOT)
       Via: 1.1 Repose (Repose/6.2.1.2)
       X-Compute-Request-Id: req-3c46ba6b-36c6-42cd-a813-df476b396161


.. code::

   {
       "virtual_interfaces": [
           {
               "id": "a589b11b-cd51-4274-8ec0-832ce799d156", 
               "ip_addresses": [
                   {
                       "address": "2001:4800:7810:0512:d87b:9cbc:ff04:850c", 
                       "network_id": "ba122b32-dbcc-4c21-836e-b701996baeb3", 
                       "network_label": "public"
                   }, 
                   {
                       "address": "64.49.226.149", 
                       "network_id": "ba122b32-dbcc-4c21-836e-b701996baeb3", 
                       "network_label": "public"
                   }
               ], 
               "mac_address": "BC:76:4E:04:85:0C"
           }, 
           {
               "id": "de7c6d53-b895-4b4a-963c-517ccb0f0775", 
               "ip_addresses": [
                   {
                       "address": "192.168.0.2", 
                       "network_id": "f212726e-6321-4210-9bae-a13f5a33f83f", 
                       "network_label": "superprivate_xml"
                   }
               ], 
               "mac_address": "BC:76:4E:04:85:20"
           }, 
           {
               "id": "e14e789d-3b98-44a6-9c2d-c23eb1d1465c", 
               "ip_addresses": [
                   {
                       "address": "10.181.1.30", 
                       "network_id": "3b324a1b-31b8-4db5-9fe5-4a2067f60297", 
                       "network_label": "private"
                   }
               ], 
               "mac_address": "BC:76:4E:04:81:55"
           }
       ]
   }
   




