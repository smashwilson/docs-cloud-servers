
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-server-servers:

Create server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /servers

Provisions a server asynchronously.

The full URL to the newly created server is returned through the ``Location`` header and is 				available as a ``self`` and ``bookmark`` link in the server representation.

The progress of the server build depends on factors including location of the requested image, network i/o, 				host load, and the selected flavor. You can check the progress of the build request by issuing a call to 				retrieve the details of the server. Once the build is complete, the server's ``status`` is ``ACTIVE``.

For OnMetal server builds, even after the ``status`` is ACTIVE, wait a few additional 				moments for the network configuration to complete. Once the new OnMetal server pings successfully, you can 				begin to use it.

.. important::
   OnMetal servers must be created using an ssh key pair. Thus you should ignore the administrator 					password returned by a Create Server operation because it does not allow access to the OnMetal server.
   
   

The following extensions allow you to use other options when creating a new server:



*  Config drive
*  Boot from volume
*  Networks for nova and for neutron
*  Key pairs




This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
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








This table shows the body parameters for the request:

+---------------------------------------------+-------------+----------------------+
|Name                                         |Type         |Description           |
+=============================================+=============+======================+
|parameters.server.\ **name**                 |String       |The server name.      |
|                                             |*(Required)* |                      |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **imageRef**             |Uuid         |The image reference   |
|                                             |*(Required)* |for the desired image |
|                                             |             |for your server       |
|                                             |             |instance.             |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\                          |Object       |The container of      |
|**block_device_mapping_v2**                  |*(Optional)* |bootable volume       |
|                                             |             |details.              |
+---------------------------------------------+-------------+----------------------+
|parameters.server.block_device_mapping_v2.\  |Integer      |The index of the      |
|**boot_index**                               |*(Optional)* |bootable volume.      |
+---------------------------------------------+-------------+----------------------+
|parameters.server.block_device_mapping_v2.\  |Integer      |The id of the         |
|**uuid**                                     |*(Optional)* |bootable volume.      |
+---------------------------------------------+-------------+----------------------+
|parameters.server.block_device_mapping_v2.\  |String       |The source type for   |
|**source_type**                              |*(Optional)* |the bootable volume.  |
+---------------------------------------------+-------------+----------------------+
|parameters.server.block_device_mapping_v2.\  |String       |The destination type  |
|**destination_type**                         |*(Optional)* |for the bootable      |
|                                             |             |volume.               |
+---------------------------------------------+-------------+----------------------+
|parameters.server.block_device_mapping_v2.\  |Boolean      |Flag to indicate      |
|**delete_on_termination**                    |*(Optional)* |whether the bootable  |
|                                             |             |volume should be      |
|                                             |             |deleted after server  |
|                                             |             |creation.             |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **flavorRef**            |Uuid         |The flavor reference  |
|                                             |*(Required)* |for the desired       |
|                                             |             |flavor for your       |
|                                             |             |server instance.      |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **config_drive**         |String       |Enables metadata      |
|                                             |*(Optional)* |injection in a server |
|                                             |             |through a             |
|                                             |             |configuration drive.  |
|                                             |             |To enable a           |
|                                             |             |configuration drive,  |
|                                             |             |specify ``true``.     |
|                                             |             |Otherwise, specify    |
|                                             |             |``false``.            |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **key_name**             |String       |The name of the key   |
|                                             |*(Optional)* |pair used to          |
|                                             |             |authenticate by using |
|                                             |             |key-based             |
|                                             |             |authentication        |
|                                             |             |instead of password-  |
|                                             |             |based authentication. |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **OS-DCF:diskConfig**    |String       |The disk              |
|                                             |*(Optional)* |configuration value.  |
|                                             |             |The image             |
|                                             |             |auto_disk_config      |
|                                             |             |metadata key set will |
|                                             |             |affect the value you  |
|                                             |             |can choose to set the |
|                                             |             |server ``OS-          |
|                                             |             |DCF:diskConfig``. If  |
|                                             |             |an image has          |
|                                             |             |``auto_disk_config``  |
|                                             |             |value of              |
|                                             |             |``disabled``, you     |
|                                             |             |cannot create a       |
|                                             |             |server from that      |
|                                             |             |image when specifying |
|                                             |             |``OS-DCF:diskConfig`` |
|                                             |             |value of ``AUTO``.    |
|                                             |             |Valid values are:     |
|                                             |             |AUTO:The server is    |
|                                             |             |built with a single   |
|                                             |             |partition which is    |
|                                             |             |the size of the       |
|                                             |             |target flavor disk.   |
|                                             |             |The file system is    |
|                                             |             |automatically         |
|                                             |             |adjusted to fit the   |
|                                             |             |entire partition.     |
|                                             |             |This keeps things     |
|                                             |             |simple and automated. |
|                                             |             |AUTO is valid only    |
|                                             |             |for images and        |
|                                             |             |servers with a single |
|                                             |             |partition that use    |
|                                             |             |the EXT3 file system. |
|                                             |             |This is the default   |
|                                             |             |setting for           |
|                                             |             |applicable Rackspace  |
|                                             |             |base images.          |
|                                             |             |MANUAL:The server is  |
|                                             |             |built using the       |
|                                             |             |partition scheme and  |
|                                             |             |file system of the    |
|                                             |             |source image. If the  |
|                                             |             |target flavor disk is |
|                                             |             |larger, the remaining |
|                                             |             |disk space is left    |
|                                             |             |unpartitioned. This   |
|                                             |             |enables images to     |
|                                             |             |have non-EXT3 file    |
|                                             |             |systems, multiple     |
|                                             |             |partitions, and so    |
|                                             |             |on, and it enables    |
|                                             |             |you to manage the     |
|                                             |             |disk configuration.   |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **metadata**             |String       |Metadata key and      |
|                                             |*(Optional)* |value pairs. The      |
|                                             |             |maximum size of each  |
|                                             |             |metadata key and      |
|                                             |             |value is 255 bytes    |
|                                             |             |each.                 |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **personality**          |Array        |The array of          |
|                                             |*(Optional)* |personality files for |
|                                             |             |the server.           |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **user_data**            |String       |Data used with        |
|                                             |*(Optional)* |config_drive for      |
|                                             |             |configuring a server. |
+---------------------------------------------+-------------+----------------------+
|parameters.server.personality.\ **path**     |String       |The path of the       |
|                                             |*(Required)* |personality file.     |
+---------------------------------------------+-------------+----------------------+
|parameters.server.personality.\ **contents** |String       |The contents od the   |
|                                             |*(Required)* |personality file.     |
+---------------------------------------------+-------------+----------------------+
|parameters.server.\ **networks**             |Array        |The array of networks |
|                                             |*(Required)* |attached to the       |
|                                             |             |server. By default,   |
|                                             |             |the server instance   |
|                                             |             |is provisioned with   |
|                                             |             |all isolated networks |
|                                             |             |for the tenant. You   |
|                                             |             |can specify multiple  |
|                                             |             |NICs on the server.   |
|                                             |             |Optionally, you can   |
|                                             |             |create one or more    |
|                                             |             |NICs on the server.   |
|                                             |             |To provision the      |
|                                             |             |server instance with  |
|                                             |             |a NIC for a ``Nova-   |
|                                             |             |network`` network,    |
|                                             |             |specify the UUID in   |
|                                             |             |the ``uuid``          |
|                                             |             |attribute in a        |
|                                             |             |``networks`` object.  |
|                                             |             |To provision the      |
|                                             |             |server instance with  |
|                                             |             |a NIC for a           |
|                                             |             |``Neutron`` network,  |
|                                             |             |specify the UUID in   |
|                                             |             |the ``port``          |
|                                             |             |attribute in a        |
|                                             |             |``networks`` object.  |
+---------------------------------------------+-------------+----------------------+
|parameters.server.networks.\ **uuid**        |Uuid         |The UUID of the       |
|                                             |*(Optional)* |``Nova-network``      |
|                                             |             |network attached to   |
|                                             |             |the server.           |
+---------------------------------------------+-------------+----------------------+
|parameters.server.networks.\ **port**        |Uuid         |The UUID of the       |
|                                             |*(Optional)* |``Neutron`` port      |
|                                             |             |attached to the       |
|                                             |             |server.               |
+---------------------------------------------+-------------+----------------------+





**Example Create server: JSON request**


.. code::

   X-Auth-Token: f064c46a782c444cb4ba4b6434288f7c
   Content-Type: application/json
   Accept: application/json


.. code::

   {
       "server": {
           "name": "api-test-server-1",
           "imageRef": "3afe97b2-26dc-49c5-a2cc-a2fc8d80c001",
           "flavorRef": "2",
           "config_drive": true,
           "OS-DCF:diskConfig": "AUTO",
           "metadata": {
               "My Server Name": "API Test Server 1"
           },
           "networks": [
               {
                   "uuid": "00000000-0000-0000-0000-000000000000"
               },
               {
                   "uuid": "11111111-1111-1111-1111-111111111111"
               }
           ]
       }
   }





Response
""""""""""""""""





This table shows the body parameters for the response:

+---------------------------+-------------------------+------------------------+
|Name                       |Type                     |Description             |
+===========================+=========================+========================+
|parameters.\ **server**    |Object                   |The container for       |
|                           |                         |server data.            |
+---------------------------+-------------------------+------------------------+
|parameters.server.\ **id** |Uuid                     |The ID of the server.   |
+---------------------------+-------------------------+------------------------+
|parameters.server.\        |Uuid                     |An array of the self    |
|**links**                  |                         |and bookmark links to   |
|                           |                         |the server.             |
+---------------------------+-------------------------+------------------------+
|parameters.server.links.\  |Uuid                     |The URL for the server  |
|**href**                   |                         |and the associated      |
|                           |                         |``rel``.                |
+---------------------------+-------------------------+------------------------+
|parameters.server.links.\  |Uuid                     |The descriptive field   |
|**rel**                    |                         |for the associated      |
|                           |                         |``href``, which is      |
|                           |                         |either ``self`` or      |
|                           |                         |``bookmark``.           |
+---------------------------+-------------------------+------------------------+
|parameters.server.\        |String                   |The password assigned   |
|**adminPass**              |                         |to provide login access |
|                           |                         |to the server.          |
+---------------------------+-------------------------+------------------------+
|parameters.server.\ **OS-  |String                   |The disk configuration  |
|DCF:diskConfig**           |                         |value. Valid values are |
|                           |                         |``AUTO`` and ``MANUAL``.|
+---------------------------+-------------------------+------------------------+







**Example Create server: JSON response**


.. code::

       Status Code: 202 Accepted
       Content-Length: 380
       Content-Type: application/json
       Date: Thu, 04 Dec 2014 18:47:30 GMT
       Location: https://dfw.servers.api.rackspacecloud.com/v2/820712/servers/4b963871-f591-4b7d-b05f-7c0286e3c50f
       Server: Jetty(8.0.y.z-SNAPSHOT)
       Via: 1.1 Repose (Repose/2.12)
       x-compute-request-id: req-b8b54344-41a9-4d6a-a92f-60f3dcab4b1f


.. code::

   {
     "server": {
       "OS-DCF:diskConfig": "AUTO",
       "id": "4b963871-f591-4b7d-b05f-7c0286e3c50f",
       "links": [
         {
           "href": "https://dfw.servers.api.rackspacecloud.com/v2/820712/servers/4b963871-f591-4b7d-b05f-7c0286e3c50f",
           "rel": "self"
         },
         {
           "href": "https://dfw.servers.api.rackspacecloud.com/820712/servers/4b963871-f591-4b7d-b05f-7c0286e3c50f",
           "rel": "bookmark"
         }
       ],
       "adminPass": "C3tfz8jQtnKC"
     }
   }




