
### **Rest Booking API Testing with Postman Newman**
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

## API Documentation:
- https://documenter.getpostman.com/view/33654656/2sA2xnyAAw
  
### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman.](https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  git clone : [((https://github.com/Jasmine3014/Automated-Testing-of-Booking-API-with-Newman-Report))]
```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```
### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
    -   Detailed test results can be viewed for each request.

## **Testing**

## Test Case Scenarios:

## _**1. Create New Booking**_

### Request URL: https://restful-booker.herokuapp.com/booking/
### Request Method: POST
### Pre-request Script:
```console 
    var firstname = pm.variables.replaceIn("{{$randomFirstName}}")
console.log(firstname)
pm.environment.set("firstname", firstname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}")
console.log(lastname)
pm.environment.set("lastname", lastname)

var totalprice = pm.variables.replaceIn("{{$randomPrice}}")
console.log(totalprice)
pm.environment.set("totalprice",parseInt(totalprice))

var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
console.log(depositpaid)
pm.environment.set("depositpaid", depositpaid)

var additionalneeds = pm.variables.replaceIn("{{$randomAlphaNumeric}}")
console.log(additionalneeds)
pm.environment.set("additionalneeds",(additionalneeds))


const date = require("moment")
const today = date()
// console.log (today.format("YYYY-DD-MM"))
var checkin = today.add(11,'d').format("YYYY-MM-DD")
console.log (checkin)
pm.environment.set("checkin", checkin)
var checkout = today.add(15,'d').format("YYYY-MM-DD")
console.log (checkout)
pm.environment.set("checkout", checkout)

```
  **Request Body:** 
 ```console 
  {
     "firstname" : "{{firstName}}",
     "lastname" : "{{lastName}}",
     "totalprice" : {{totalPrice}},
     "depositpaid" : {{depositPaid}},
     "bookingdates" : {
   	  "checkin" : "{{checkin}}",
   	  "checkout" : "{{checkout}}"
     },
     "additionalneeds" : "{{additionalNeeds}}"
 }

```
  **Response Body:**
 ```console 
  {
    "bookingid": 62,
    "booking": {
        "firstname": "Amaya",
        "lastname": "Volkman",
        "totalprice": 893,
        "depositpaid": true,
        "bookingdates": {
            "checkin": "2024-03-29",
            "checkout": "2024-04-13"
  }

```
 ## _**2. Get Booking Details By ID**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: GET
### Response Body:
 ```console 
  {
      "firstname": "Cora",
      "lastname": "McLaughlin",
      "totalprice": 855,
      "depositpaid": false,
      "bookingdates": {
          "checkin": "2024-03-29",
          "checkout": "2024-04-13"
      },
      "additionalneeds": "l"
  }

```
## _**3. Create A Token For Authentication.**_
### Request URL: https://restful-booker.herokuapp.com/auth
### Request Method: POST
### Pre-request Script: None
### Request Body:
 ```console 
{
	"username": "admin",
	"password": "password123"
}
```
  **Response Body:**
 ```console 
{
   "token": "9a095b0bda6b4f8"
}
```

 ## _**4. Update the Booking Details**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
```console 
  var firstname = pm.variables.replaceIn("{{$randomFirstName}}")
  console.log(firstname)
  pm.environment.set("firstname", firstname)
  
  var lastname = pm.variables.replaceIn("{{$randomLastName}}")
  console.log(lastname)
  pm.environment.set("lastname", lastname)
  
  var totalprice = pm.variables.replaceIn("{{$randomPrice}}")
  console.log(totalprice)
  pm.environment.set("totalprice",parseInt(totalprice))
  
  var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
  console.log(depositpaid)
  pm.environment.set("depositpaid", depositpaid)
  
  var additionalneeds = pm.variables.replaceIn("{{$randomAlphaNumeric}}")
  console.log(additionalneeds)
  pm.environment.set("additionalneeds",(additionalneeds))
  
  
  const date = require("moment")
  const today = date()
  // console.log (today.format("YYYY-DD-MM"))
  var checkin = today.add(11,'d').format("YYYY-MM-DD")
  console.log (checkin)
  pm.environment.set("checkin", checkin)
  
  var checkout = today.add(15,'d').format("YYYY-MM-DD")
  console.log (checkout)
  pm.environment.set("checkout", checkout)

```
  **Request Body:** 
 ```console 
   {
     "firstname" : "{{firstName}}",
     "lastname" : "{{lastName}}",
     "totalprice" : {{totalPrice}},
     "depositpaid" : {{depositPaid}},
     "bookingdates" : {
   	  "checkin" : "{{checkin}}",
   	  "checkout" : "{{checkout}}"
     },
     "additionalneeds" : "{{additionalNeeds}}"
 }

```
  **Response Body:**
 ```console 
 {
    "bookingid": 2246,
    "booking": {
        "firstname": "Quinten",
        "lastname": "Kuphal",
        "totalprice": 468,
        "depositpaid": true,
        "bookingdates": {
            "checkin": "2024-03-29",
            "checkout": "2024-04-13"
        },
        "additionalneeds": "5"
    }
}

```

 ## _**5. Delete Booking Record**_

### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: DELETE
### Response Body: None 

## Run Command:  
- Run Command for Console: 
```console 
newman run Booking.postman_collection.json -e Booking.postman_environment.json 
```
- Run Command for Report: 
```console 
newman run Booking.postman_collection.json -e Booking.postman_environment.json -r cli,htmlextra
```

## Newman Report Summary:

![image](https://github.com/Jasmine3014/Automated-Testing-of-Booking-API-with-Newman-Report/assets/59429546/c3f79af2-5b03-4ffd-b6b5-0e369192b0f8)
![image](https://github.com/Jasmine3014/Automated-Testing-of-Booking-API-with-Newman-Report/assets/59429546/634af290-ce66-4311-92f7-3fe206f26116)
![image](https://github.com/Jasmine3014/Automated-Testing-of-Booking-API-with-Newman-Report/assets/59429546/de3c3e0c-0cf8-4b65-aa9a-c927be508a0d)
![image](https://github.com/Jasmine3014/Automated-Testing-of-Booking-API-with-Newman-Report/assets/59429546/b2c748ec-ce72-4fd1-a4a1-3f2bd7ef9db2)







