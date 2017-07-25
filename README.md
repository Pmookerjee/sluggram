SLUGGRAM
===
> a social photo platform REST API

## API Resources
###### User
The user model is used in the backend strickly for authentication and authorization. The user model will never be returned from the API, however userID's are stored on Profiles, Photos, and Comments for authorzation validation.  

**User Model**  
* `_id` - an unique database genorated string which uniqly identifys a user
* `email` - a unique string which stores the users email
* `username` - a unique string that stores the users username
* `passwordHash` - a string that holds a users hashed password
* `tokenSeed` - a unique and random string used to genorate authorization tokens 

###### Profile
Each user can have a single profile. Authorization is required for Creating, Updating, and Deleteing Profiles but they have public read access.  

**Profile Model**  
* `_id` - an unique database genorated string which uniqly identifys a profile  
* `owner` - the user id of the profiles creator 
* `email` - a unique string which stores the profiles email
* `username` - a unique string that stores the profiles profilename
* `avatar` - a string holding a URL to a profile photo
* `bio` - a string holding a profiles bio 

###### Photo
Authorization is required for Creating, Updating, and Deleteing Photos but they have public read access.

**Photo Model**  
* `_id` - an unique database genorated string which uniqly identifys a profile  
* `owner` - the user id of the photos creator 
* `profile` - stores a the creators profile ID. the profile is populated on GET requests
* `comments` - stores an array of comment IDs. the comments are populated on GET requests
* `url` - a string which store a url to the photo
* `description` - a string with a description of the photo

###### Comment
Authorization is required for Creating, Updating, and Deleteing Comments but they have public read access.

**Comment Model**
* `_id` - an unique database genorated string which uniqly identifys a profile  
* `owner` - the user id of the photos creator 
* `profile` - stores a the creators profile ID. the profile is populated on GET requests
* `photoID` - stores the photo id of the photo the comment is a response to 
* `content` - a string with the users comment

## Auth 
Sluggram uses Basic authentication and Bearer authorization to enforce access controls. Basic and Bearer auth both use the HTTP `Authorization` header to pass credentials on a request.

#### Basic Authentication
Once a user account has been created. Basic Authentication can be used to make a request on behalf of the account. To create a Basic Authorzation Header the client must base64 encode a string with the username and password seporated by a colon. Then the encoded string can then be appened to the string `'Basic '` and set to an `Authorization` header on an HTTP Request.    

``` javascript
// Example of formating a Basic Authentication in Javascript 
let username = 'slugbyte'
let password = 'abcd1234'

let encoded = window.btoa(`${username}:${password}`)
let headers = {
  Authorization: `Basic ${encoded}`
}
```

#### Bearer Authorization


#### POST `/login`

#### GET `/signup`

## Profiles
#### POST `/profiles`
#### GET `/profiles`
#### GET `/profiles/:id`
#### PUT `/profiles/:id`
#### DELETE `/profiles/:id`

## Photos 
#### POST `/photos`
#### GET `/photos`
#### GET `/photos/:id`
#### PUT `/photos/:id`
#### DELETE `/photos/:id`

## Comments
#### POST `/comments`
#### GET `/comments`
#### GET `/comments/:id`
#### PUT `/comments/:id`
#### DELETE `/comments/:id`
