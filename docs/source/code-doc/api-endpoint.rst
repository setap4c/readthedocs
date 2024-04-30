API Endpoints
=============

.. note::
    This documentation only covers API endpoints which have been implemented fully and are in use throughout the application.

/v1/user/get-info
-----------------

GET request to return the user's information.

Required Query Parameters:
- :code:`userId`

Required Headers
- :code:`authorization`

Example Request:

:code:`/v1/user/get-info?userId=3`