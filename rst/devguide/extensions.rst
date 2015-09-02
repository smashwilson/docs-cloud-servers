==========
Extensions
==========

Rackspace has implemented several Cloud servers extensions, which provide either new 
functionality or enhanced functionality for existing operations. You can list 
available extensions and get details for a specific extension.

Extended Responses and Actions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use extensions to define new data types, parameters, actions, headers,
states, and resources.


.. important::
   Applications should be prepared to ignore response data that
   contains extension elements. An extended state should always be treated as
   an ``UNKNOWN`` state if the application does not support the extension.
   Applications should also verify that an extension is available before
   submitting an extended request.


Extensions API operations
~~~~~~~~~~~~~~~~~~~~~~~~~
Using API operations, users and applications can programmatically determine which extensions 
are available, either by listing them or getting details for a specific extension.

Click the following links to see examples of these operations.

.. toctree::
    :maxdepth: 2
    
    List extensions <api-operations/supporting/get-retrieve-list-of-extensions-extensions>
    Get details for specified extension <api-operations/supporting/get-retrieve-details-for-the-specified-extension-extensions-alias>