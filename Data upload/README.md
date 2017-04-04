# Uploading to Car & Away
This document will explain how to upload files to the Car & Away system.

## Security
All calls to the API are monitored and only calls with a valid security token will be processed. Pass your token in as a 'code' query parameter.

## File format
The file you upload to the system must be a CSV file with the following fields:
- Booking_Ref
- Booking_Status
- Car_Park_Code
- Product_Name
- Car Care Extra
- Booking_Start_Date
- Booking_End_Date
- Reg_No
- Veh_Mfr
- Veh_Model
- Veh_Colour
- Flight_No_Out
- Booking_Start_Time
- Booking_End_Time
- Lead_Name
- Customer_Mobile
- Customer_Email
- Flight_No_In,Source_Reference
- Sms_Confirmation

The first line must be the field titles, after that each line of the file represents a single record to be inserted. Not every field is required but *Booking_start_date, Booking_end_date, reg_no, booking_start_time, booking_end_time, customer_email* are required.

You can [download the sample CSV file](SampleUpload.csv) to see what a valid upload file should look like.

## End Point
The end point for this service is **/api/DataFeed**. There is also a[ swagger definition file](swagger.json) if needed.

### Method
- POST

### Query string parameter:
- code : your secret token for accessing the system

### Form parameters
- File data : You only need to send in the file as form data for it to be processed

### Return code
- 200 (OK) : Means the file was processed successfully
- 401 (Unauthorised) : The security token was incorrect
- Anything else means there was a problem

## Development
You are free to call the development environment as much as you need.

The development environment URL is: <http://carandaway.westeurope.cloudapp.azure.com:600> and the DataFeed API is available here: <http://carandaway.westeurope.cloudapp.azure.com:600/api/DataFeed>