# Car & Away Search
This document will show you how to search against Car & Away availability and get results.

## Definition
The search API conforms to this [swagger API definition](SearchApiSwagger.yaml).

## Security
The API uses [JWT (JSON Web Tokens)](https://jwt.io/) as its way of identifying users of the API. You will be issued with a username and password so you can use the API.

### Get a token
In order to use the API you will need to login with your username and password to receive a new token.

/api/Login?code={CODE}&username={USERNAME}&password={PASSWORD}

If your username and password are correct you will receive a 200 OK response with a message payload that contains your token. Any incorrect attempts will return a 400 Bad Request response. There will be no indication of what went wrong, a user with an incorrect password gets the same message as a user who doesn't exist.

## Searching
To search make a GET request to the URL and pass the following query parameters:
- requestId: string - Required
- pickUpDate: Date - Required
- dropOffDate: Date - Required
- pickUpLat: number
- pickUpLon: number
- pickUpRadius: number
- pickUpLocationId: string
- dropOffLocationId: string
- maxVehicles: number
- driverAge: number
- supplierCode: string
- supplierReservationReference: string
- accountNumber: string
- rateCode: string
- discountNumber: string
- rateReference: string

Not all of these fields are required and you can search in many different combinations

### Security
As previously stated the API uses JWT as its form of protection. You will need to provide your valid JWT as part of the requests header to be able to use the service. As per the specification for JWT provide your token in the Authorization header of your request.

If the token isn't presented a 403 Bad Request response will be returned. The message will contain a JSON object with a code of 1051 and a message of "No authentication token".

If a token is presented but it isn't valid then a 403 Bad Request response will be returned. The message will contain a JSON object with a code of 1052 and a message of "Invalid authentication token".

### Example searches
#### Search between 20/5/17 11:30 - 23/5/17 12:00 at LGW
/api/RentalCarsSearch?code={CODE}=&pickUpDate=2017-05-20 11:30:00&dropOffDate=2017-05-23 12:00:00&pickUpLocationId=LGW

This will return a 200 OK with the message payload as a JSON object.

#### Search between 20/5/17 9:00 - 24/5/17 18:00 at LGW lat/lon location
/api/RentalCarsSearch?code={TOKEN}&pickUpDate=2017-05-21 11:30:00&dropOffDate=2017-05-23 12:00:00&pickUpLat=51.1536621&pickUpLon=-0.1820629&pickUpRadius=50

This will return a 200 OK with the message payload as a JSON object

## Development environment
The development environment for testing is available here.

https://carandawaysearch.azurewebsites.net

