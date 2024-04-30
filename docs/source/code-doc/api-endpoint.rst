API Endpoints
=============

.. note::
    This documentation only covers API endpoints which have been implemented fully and are in use throughout the application.

/v1/user/get-info
-----------------

GET request to return the user's information.

Required Query Parameters:
- :code:`userId`

Required Headers:
- :code:`authorization`

Example Request:

:code:`/v1/user/get-info?userId=3`

/v1/user/create
---------------

POST request to create a new user on EcoTracker, called by Auth0.

Required Query Parameters:
- :code:`username`
- :code:`displayName`
- :code:`dob`
- :code:`email`
- :code:`authId`

Required Headers:
- None

Example Request:

:code:`/v1/user/create?username=dave&displayName=fred&dob=2024-04-03&email='dave@juiceofthecat.com'&authId=3456`

Example Response:
::
    {
        "accountId": 29
    }


/v1/journey/log
---------------

POST request to log a journey as completed to the database.

Required Query Parameters:
- :code:`userId`
- :code:`emissionId`
- :code:`startPostcode`
- :code:`endPostcode`
- :code:`distance`

Required Headers:
- None

Example Request:

:code:`/v1/journey/log?userId=1&emissionId=1&startPostcode=PO1 2EF&endPostcode=PO1 2UP&distance=1.232`

Example Response:
::
    ok


/v1/journey/save
----------------

POST request to log a journey as saved to the database

Required Query Parameters:
- :code:`userId`
- :code:`emissionId`
- :code:`startPostcode`
- :code:`endPostcode`
- :code:`distance`

Required Headers:
- None

Example Request:

:code:`/v1/journey/save?userId=1&emissionId=1&startPostcode=PO1 2EF&endPostcode=PO1 2UP&distance=1.232`

Example Response:
::
    ok

/v1/journey/get-saved
---------------------

GET request to retrieve all saved journeys of a specified user

Required Query Parameters:
- :code:`userId`

Required Headers:
- None

Example Request:

:code:`/v1/journey/get-saved?userId=1`

Example Response:
::
    [
        {
            "emission_id":1,
            "start_post":"PO1 1DZ",
            "end_post":"PO1 2SE",
            "distance":1.2319999933242798,
            "log_time":"2024-04-20 19:35:44.080912Z"
        },
        {
            "emission_id":3,
            "start_post":"PO1 1DZ",
            "end_post":"PO1 2GP",
            "distance":1.2319999933242798,
            "log_time":"2024-04-24 09:29:51.254858Z"}
    ]