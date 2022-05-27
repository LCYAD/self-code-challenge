# Self Code Challenge

This is to hold the documentation for my own personal code challenge for different language or framework to test out

## Backend API Challenge

### The Task
* make 2 endpoints that allow getting and setting quotations in the redis
* The setting quotation endpoint should be able to take in multiple quotations


### Get Quotation By Id

* The response JSON should look like the following:

```json
{
    "quotationId": "182379172831",
    "expireAt": "2021-09-10T03:40:51.000Z",
    "scheduleAt": "2021-09-10T03:40:51.000Z",
    "deliveryBy": "2021-09-11T03:40:51.000Z",
    "stops": [
    {
        "coordinates": {
            "lat": "22.3353139",
            "lng": "114.1758402"
        },
        "address": "999 Prince Edward Road"
    },
    {
        "coordinates": {
            "lat": "22.3353139",
            "lng": "114.1758402"
        },
        "address": "InnoCentre, 72 Tat Chee Avenue"
    }
    ],
    "location": "Hong Kong",
    "item": {
        "quantity": 1,
        "weight": 3,
        "categories": [
            "GLASS"
        ],
        "handlingInstructions": [
            "FRAGILE"
        ]
    }
}
```
* the error if quotation not found are
```json
{
    "code": "10004",
    "message": "RESOURCES_NOT_FOUND",
    "detail": "Quotation not found"
}
```
### Create Quotations

* should handle cases where body is empty with validation error
* The request JSON should look like the following:

```json
[
    {
        "scheduleAt": "2021-09-10T03:40:51.000Z",
        "deliveryBy": "2021-09-11T03:40:51.000Z",
        "stops": [
        {
            "coordinates": {
                "lat": "22.3353139",
                "lng": "114.1758402"
            },
            "address": "999 Prince Edward Road"
        },
        {
            "coordinates": {
                "lat": "22.3353139",
                "lng": "114.1758402"
            },
            "address": "InnoCentre, 72 Tat Chee Avenue"
        }
        ],
        "location": "Hong Kong",
        "item": {
            "quantity": 1,
            "weight": 3,
            "categories": [
                "GLASS"
            ],
            "handlingInstructions": [
                "FRAGILE"
            ]
        }
    }
]
```
* Notes on fields
    * `quotationId` is a unique Id made of 12 digits
    * `coordinates` can be optional but if available then `lat`, `lng` must be available and match the relevant string format
    * `categories` and `handlingInstructions` fields are required but can be empty
    * All date time related input need to match the relevant standard on date time string
    * `scheduleAt` should always be before `deliveryBy`
* The response JSON should look like the following:

```json
[
    {
        "quotationId": "182379172831",
        "expireAt": "2021-09-10T03:40:51.000Z",
        "scheduleAt": "2021-09-10T03:40:51.000Z",
        "deliveryBy": "2021-09-11T03:40:51.000Z",
        "stops": [
        {
            "coordinates": {
                "lat": "22.3353139",
                "lng": "114.1758402"
            },
            "address": "999 Prince Edward Road"
        },
        {
            "coordinates": {
                "lat": "22.3353139",
                "lng": "114.1758402"
            },
            "address": "InnoCentre, 72 Tat Chee Avenue"
        }
        ],
        "location": "Hong Kong",
        "item": {
            "quantity": 1,
            "weight": 3,
            "categories": [
                "GLASS"
            ],
            "handlingInstructions": [
                "FRAGILE"
            ]
        }
    }
]
```

### Errors
* The endpoint requires a JWT validation to be used, if not provided throw error
```json
{
    "code": "10002",
    "message": "UNAUTHORIZED",
    "detail": "You are not authorized to access this endpoint"
}
```
* Validation Error (HTTP error `422`) should be like follows

```json
{
    "code": "10003",
    "message": "VALIDATION_ERROR",
    "detail": "<details here>"
}
```

* API Route Not Found should look like
```json
{
    "type": "API_ROUTE_NOT_FOUND",
    "code": "10001",
    "detail": "Request API route does not exist"
}
```


### Things should be included
* JWT Authorized authorization
* Swagger Documentation
* should be able to be Dockerized, can be used for K8S or mini-kube
* Include testing, both unit and integration test (> 80%)
* Detailed documentation on how to setup and boot the repository
* Detail Logging and Trace and Metrics via Open Telemetry or other implementation
* Instructions on how to easily setup debugging