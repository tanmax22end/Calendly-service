# Test_Project_3

   1. GET '/' endpoint: This endpoint is used to handle the root URL request. 
   
      It generates an authorization URL using the Google OAuth2 client and sends it as a response. 
   
      The user needs to visit this URL and authenticate with their Google account to obtain an authorization code, which can then be used to get access tokens for         making authorized API requests.

   2. POST '/add' endpoint: This endpoint is used to handle the addition of new slots for a host. 
   
      It expects a JSON payload in the request body containing the host ID and details of the slots to be added. 
   
      It first checks if the host already exists in the database. If it does, it appends the new slots to the existing host's details. 
   
      If it doesn't exist, it redirects to the authorization URL for authentication, and upon successful authentication, creates a new host with the provided slots         and saves it to the database.

   3. GET '/availability/:hostId' endpoint: This endpoint is used to fetch the availability of slots for a specific host by host ID. It expects the host ID as a URL       parameter. 
   
      It queries the database to find the host with the provided host ID and retrieves the available slots (slots with 'status' field as false) from the host's             details. It then sends the available slots as a JSON response.

   4. POST '/meet' endpoint: This endpoint is used to handle the creation of a meeting request. 
   
      It expects a JSON payload in the request body containing the host ID, user ID, start time, end time, summary, and location of the meeting. 
   
      It first checks if the host and user exist in the database. 
   
      If the user doesn't exist, it redirects to the authorization URL for authentication, and upon successful authentication, creates a new user with the provided         user ID and credentials, and a new host with empty details. 
   
      Then, it checks if the requested time slot is available in the host's details. If it is, it updates the host's details with the booked slot, and sends a             success response. If it's not available, it sends an error response.
   
