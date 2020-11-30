# mytravel-experience-api

## About the project

mytravel-experience-api is an experience layer API which is used to provide train services information to the end users. 
Also, this api get inforamtion needed for travel such as weather information, tourist attraction sites, resturants and supermarket location.
It uses two process APIs to create, retrive, and update data for train service operation. 

The two process API used are:

 **1. MyTrain Process API**
      
      This API is used to to add or retrive data related to train services. The operations provided by this API are:
      
      - Allow user to register and subscribe for train service 
      - Get a User detail, specific subscription detail, and list of subscription for a user
      - Request forgot password
      - Validate user
      - Provide train service and train detail information. 
 
 **2.  Notification Process API**
      
       This API is used to provide information related to delay or cancelled train service along with weather and covid records. The operations that are provided by the API are:
       
       - retrive current weather information,
       - get active covid status,
       - list point of interest such as restaurants, supermarket, and
       - notify users based about the train delay or cancellation

## List of endpoints

**1. User registration**

     It is used to register.
     Resource: */myTravel/register*
     Method: POST
     Input: As payload these fields are: First Name, Last Name, Email, Phone, Password
     
**2. User login**
     
     This method is used to create token for login details
     Resource: */myTravel/register*
     Method: POST
     Input: As payload user need to enter Email and password
     
**3. Forgot Password**

     This allows use to request for the new password. 
     Resource: */myTravel/forgotPassword*
     Method: POST
     Input: As payload user need to valid Email ID
    
 **4. Get specific user information**
 
      Used to retrive user detail for a sepcific user
      Resource: */myTravel/users/{userId}*
      Method:  GET
      URI parameter: A valid user id must be used for successful authorization
      
 **5. User subscription**
 
      It allows to create, retrive and delete subscription information  
      Resources to achieve the operation are: 
      - */myTravel/users/{userId}/subscriptions*
         Methods: GET, POST
         Input: Must pass a valid userid as URI parameter
         
      - */myTravel/users/{userId}/subscriptions/{subscriptionId}*
         Methods: GET, DELETE
         Input: Must pass a valid userid and subscriptionId as URI parameter
        
 **6. Location Information**
      This provides information realted to the location like get all station information, get service information for specific date, 
      list point of interest, and list nearby stations.
      
      All the operation uses GET method. The operations available to get station or service information are:
      - */myTravel/locations/stations*
            list all the station
            Example: http://mytravel-experience-api.us-e2.cloudhub.io/api/myTravel/locations/stations
            
      - */myTravel/locations/stations/nearby*
           Query parameter: To search nearby station user need to pass the 'address' as query parameter
           Example: http://mytravel-experience-api.us-e2.cloudhub.io/api/myTravel/locations/nearby?address=London Waterloo
           
      - */myTravel/locations/stations/trains*
           Query parameter: origin, originType, destination, destType, travelDate
           Example: http://mytravel-experience-api.us-e2.cloudhub.io/api/myTravel/locations/stations/trains?origin=Waterloo&originType=L&destination=Basingstoke&destType=L&travelDate=2020-11-30
            
      - */myTravel/locations/attractionspots*
           Query parameter: To search nearby station user need to pass the 'address' as query parameter
           Example: http://mytravel-experience-api.us-e2.cloudhub.io/api/myTravel/locations/attractionspots?city=Basingstoke
 
 **7. Weather Information**
      
      It provides the weather forecast information for provided destination date.
      Resource: */myTravel/locations/forecast*
      Method:  GET
      Query parameter: mandatory fields: city, date,  optional fields: countryCode, units
      Example: http://mytravel-experience-api.us-e2.cloudhub.io/api/myTravel/locations/forecast?city=Leeds&date=2020-11-1

**8. COVID Information**

     This is used to provides COVID information like new cases, death cases, and toatal cases based on boundary.
     Method:  GET
     Resources:
      - */myTravel/locations/covid*
         Get the COVID information based on the country. 
         Example: http://mytravel-experience-api.us-e2.cloudhub.io/api/myTravel/locations/covid
      
      - */myTravel/locations/covid/areaname*
         Get COVID details information based on the region or areaname.
         Example: http://mytravel-experience-api.us-e2.cloudhub.io/api/myTravel/locations/covid/areaname   
