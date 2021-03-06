
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-retrieve-list-of-server-actions-servers-server-id-os-instance-actions:

Retrieve list of server actions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /servers/{server_id}/os-instance-actions

Retrieve list of server actions.

This operation returns a list of available server actions.



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




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{server_id}               |Uuid                     |The UUID for the server. |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Retrieve list of server actions: JSON request**


.. code::

   X-Auth-Token: f064c46a782c444cb4ba4b6434288f7c
   Content-Type: application/json
   Accept: application/json





Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------------------+-------------------+-------------------+
|Name                                  |Type               |Description        |
+======================================+===================+===================+
|parameters.\ **instanceActions**      |Array              |An array of        |
|                                      |                   |instance action    |
|                                      |                   |containers of      |
|                                      |                   |action log entries |
|                                      |                   |for a server.      |
+--------------------------------------+-------------------+-------------------+
|parameters.instanceActions.\          |String             |The type of action |
|**action**                            |                   |taken.             |
+--------------------------------------+-------------------+-------------------+
|parameters.instanceActions.\          |Uuid               |The server UUID    |
|**instance_uuid**                     |                   |where the action   |
|                                      |                   |took place.        |
+--------------------------------------+-------------------+-------------------+
|parameters.instanceActions.\          |Uuid               |The action log     |
|**message**                           |                   |message, if any.   |
+--------------------------------------+-------------------+-------------------+
|parameters.instanceActions.\          |Uuid               |The project id.    |
|**project_id**                        |                   |                   |
+--------------------------------------+-------------------+-------------------+
|parameters.instanceActions.\          |Uuid               |The action request |
|**request_id**                        |                   |id.                |
+--------------------------------------+-------------------+-------------------+
|parameters.instanceActions.request_id |Datetime           |The date and time  |
|                                      |                   |that the actin     |
|                                      |                   |began.             |
+--------------------------------------+-------------------+-------------------+
|parameters.instanceActions.\          |String             |The id of the user |
|**user_id**                           |                   |who requested the  |
|                                      |                   |action.            |
+--------------------------------------+-------------------+-------------------+







**Example Retrieve list of server actions: JSON response**


.. code::

   {
       "instanceActions": [
           {
               "action": "reboot",
               "instance_uuid": "86cf2416-aaa7-4579-a4d7-0bfe42bfa8ff",
               "message": null,
               "project_id": "453265",
               "request_id": "req-7b6f6a5e-daf7-483e-aea5-a11993d1d357",
               "start_time": "2013-08-15T21:40:42.000000",
               "user_id": "35746"
           },
           {
               "action": "create",
               "instance_uuid": "86cf2416-aaa7-4579-a4d7-0bfe42bfa8ff",
               "message": null,
               "project_id": "453265",
               "request_id": "req-920c6627-c8c9-4d02-9d3d-81917e5586df",
               "start_time": "2013-07-12T21:35:37.000000",
               "user_id": "35746"
           }
       ]
   }




