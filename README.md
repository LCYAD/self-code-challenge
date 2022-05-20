# Self Code Challenge

This is to hold the documentation for my own personal code challenge for different language or framework to test out

## Backend API Challenge

### The Task
* make 2 endpoints that allow getting and setting a quotation in the redis
* The request JSON should look like the following:

```json
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
```

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
* The endpoint requires a JWT validation to be used, if not provided throw error
```json
{
    "code": "10000",
    "message": "UNAUTHORIZED",
    "detail": "You are not authorized to access this endpoint"
}
```
* the error if quotation not found are
```json
{
    "code": "10001",
    "message": "NOT_FOUND",
    "detail": "Quotation not found"
}
```

### Things should be included
* JWT Authorized authorization
* JSON validation
* Swagger Documentation
* should be able to be Dockerized, can be used for K8S or mini-kube
* Include testing, both unit and integration test (> 80%)
* Detailed documentation on how to setup and boot the repository