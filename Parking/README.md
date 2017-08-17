# Parking File
When bookings are created or cancelled a parking file will be created and sent to the right API. This will contain details of the booking that need to be handled.

## Scenarios
There are a number of scenarios that need to be handled

### Renter booking created
When a renter books out a car [this file](Simple_Rental.csv) will be created to show the when the lender vehicle needs to be made available.

### Cancel a rental
If a rental is cancelled for any reason [this file](Cancel_Rental.csv) will be sent removing the original record.

### Cancel a booking with rentals
If a booking is cancelled that does have bookings associated with it then [this file](Cancel_Booking_With_Rental.csv) will be sent to cancel both bookings at the same time.