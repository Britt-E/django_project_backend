# Django Project Back End
Brittany Evans

## Planning:
### Concept/Name
A freelancing platform that connects businesses with independent professionals in tech and design. It offers a space for companies to post jobs and for freelancers to showcase their skills and submit project proposals.

### Intended Audience/User Stories
- Businesses hiring for a project
- Freelancers looking for work

### Front End Pages/Functionality
- Home Page
    - Log In/Create Account
    - Display all projects
    - Click project to view project detail
- Project Pages
    - Project Description
    - About the client
    - Features such as hours, duration, project type
    - Skills and expertise
- User Profile
    - Update profile
    - Search projects
    - Submit a pledge

### Create A New User
1. Create a new HTTP request - POST
2. URL: https://django-britt-c5e00d2fa1ad.herokuapp.com/users/
3. Request Body -> JSON. Enter required user details in JSON:
    
        {
            "username": "{username}",
            "password": "{password}",
            "email": "{email}"
        }
4. Success code 201.

Create A Token
1. Create a new HTTP Request - POST
2. URL: https://django-britt-c5e00d2fa1ad.herokuapp.com/api-token-auth/
3. Request Body -> JSON. Enter the username and password of a user you want to generate a token for:

       {
		"username": "{username}",
		"password" : "{password}"
	    }
5. Sucess code 200.
6. Enter this token in Auth -> Bearer Token for any requests that require authentication. 
   - Token = [user_token]
   - Prefix = Token
  
### Create a New Project
1. Create a new HTTP request - POST
2. URL: https://django-britt-c5e00d2fa1ad.herokuapp.com/projects/
3. Request Body -> JSON. Enter project details in JSON:

        {
            "title": "title",
            "description": "description",
            "goal": amount,
            "image": "image_URL",
            "is_open": true/false,
            "date_created": "ISO 8601 string"
        }
   
### API Spec

| URL                    | HTTP METHOD | PURPOSE                 | REQUEST BODY   | SUCCESS RESPONSE CODE | AUTHENTICATION/AUTHORISATION                       |
| ---------------------- | ----------- | ----------------------- | -------------- | --------------------- | -------------------------------------------------- |
| /projects/             | GET         | Return all projects     | N/A            | 200                   | N/A                                                |
| /projects/:id          | GET         | Return a project by id  | N/A            | 200                   | N/A                                                |
| /projects/             | POST        | Create a new project    | Project object | 201                   | Login required                                     |
| /projects/:id          | PUT         | Update the project      | Project object | 200                   | Login required /Must be the project owner          |
| /projects/:id          | DELETE      | Delete the project      | N/A            | 200                   | Login required /Must be the project owner          |
|                        |             |                         |                |                       |                                                    |
| /pledges/              | GET         | Return all pledges      | N/A            | 200                   | N/A                                                |
| /pledges/:id           | GET         | Return a pledge by id   | N/A            | 200                   | N/A                                                |
| /pledges/              | POST        | Create a pledge         | Pledge object  | 201                   | Login required                                     |
| /pledges/:id           | PUT         | Update a pledge         | Pledge object  | 200                   | Login required /Must be the project owner          |
| /pledges/:id           | DELETE      | Delete a pledge by id   | N/A            | 200                   | Login required /Must be the project owner          |
|                        |             |                         |                |                       |                                                    |
| /users/                | GET         | Returns all users       | N/A            | 200                   | N/A                                                |
| /users/                | POST        | Create user account     | User object    | 201                   | N/A                                                |
| /users/login           | POST        | Login                   | User object    | 201                   | N/A                                                |
| /users/:id             | PUT         | Update the user by id   | User object    | 200                   | Login required /Must be the project owner          |
| /users/:id             | DELETE      | Delete the user by id   | N/A            | 200                   | Login required /Must be the project owner          |

### DB Schema
![]( db_schema.png )

### INSOMNIA
Successful GET request
![]( crowdfunding/images/GETusers.png )

Successful POST request
![]( crowdfunding/images/POSTproject.png )

Successful TOKEN return
![]( crowdfunding/images/returntoken.png )
