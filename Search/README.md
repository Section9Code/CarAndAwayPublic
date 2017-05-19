# Car & Away Search
This document will show you how to search against Car & Away availability and get results.

## Definition
The search API conforms to this [swagger API definition](PeerToPeerSearchApiSwagger.md).

## Security
> **Please note:** A JWT approach is being developed at the moment. In the mean team please use the token in the query string to get results. This page will be updated when the JWT approach is available.

You will be issued with a secure token that you will pass with every request.

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

### Example searches
#### Search between 20/5/17 11:30 - 23/5/17 12:00 at LGW
/api/RentalCarsSearch?code={TOKEN}=&pickUpDate=2017-05-20 11:30:00&dropOffDate=2017-05-23 12:00:00&pickUpLocationId=LGW

This will return a 200 OK with the message payload as a JSON object.

#### Search between 20/5/17 9:00 - 24/5/17 18:00 at LGW lat/lon location
/api/RentalCarsSearch?code={TOKEN}&pickUpDate=2017-05-21 11:30:00&dropOffDate=2017-05-23 12:00:00&pickUpLat=51.1536621&pickUpLon=-0.1820629&pickUpRadius=50

This will return a 200 OK with the message payload as a JSON object

## Development environment
The development environment for testing is available here.

https://carandawaysearch.azurewebsites.net

