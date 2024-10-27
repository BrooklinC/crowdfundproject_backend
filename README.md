# crowdfundproject_backend

# Project Title
__The Golden Goose__

## Planning:
### Concept/Name
The Golden Goose is a crowdfunding platform designed specifically to support future Olympians and Paralympians by helping them fund their training, equipment and competition expenses. It allows athletes that otherwise may not receive funding or corporate sponsorships 

### Intended Audience/User Stories
**Intended Audience:**

**Athlete Creators:** Individual Athletes can create detailed profiles and campaigns showcasing their goals, achievements and funding needs. 

**Pledges:** People interested in supporting individual athletes directly and transparently.

**User Stories:**
*As an Athlete Creator*, I want to be able to setup my project with my profile, goals and funding needs to feature on The Golden Goose and elicit potential pledgers. 

*As a Pledger*, I want to browse a curated or filtered list of Athletes to be able to find and support Athletes either in sports or with stories that interest me. 

*As a Pledger*, I want to be able to pledge money either as a once off or on a rewards tier where I'm subject to reward tiers.

*As an Athlete*, I want to be able to provide updates to my Pledgers and also provide access to exclusive tiered content. 

*As a Pledger*, I want to receive notifications/updates from the Athletes I support.


### Front End Pages/Functionality
- **Home Page:**
    - Highlights featured projects
    - Showcases The Golden Goose's unique value proposition
    - Has a call to action for Athletes and Pledges to sign up
- **Project Listing Page:**
    - Displays an outline of the individual Athlete's, their goals and funding targets
    - Allows users to scroll through and select Athlete's projects they want to review in further detail
- **User Registration/Login:**
    - Allows users to sign up using email address
    - Provides login functionality for returning users
- **About/FAQ/Contact:**
    - Provides About Us Info about The Golden Goose
    - Provides Frequently Asked Questions for users
    - Provides a Contact Form for users to get in touch with customer support

### Heroku Deployed App Link
https://git.heroku.com/golden-goose-01.git

### API Spec
| URL | HTTP Method | Purpose | Request Body | Expected Response Code | Authentication/Authorisation | Status |
| ---| ----------- | ------- | ------- | ------------ | --------------------- | ---------------------------- |
| http://127.0.0.1:8000/users/ | POST | Register a New User | {"username", "email", "password"} | 201 | N/A | PASS |
| http://127.0.0.1:8000/users/     | GET | Retrieve a list of users  | N/A  | 200 | Authenticated Admin | PASS |
| http://127.0.0.1:8000/users/:id/     | GET  | Retrieve user profile by ID  | N/A | 200 | Authenticated User or Admin | PASS |
| http://127.0.0.1:8000/users/:id/ | PUT | Update user profile by ID | {"username", "email", "first_name", "last_name"} | 200 | Authenticated User or Admin | PASS |
| http://127.0.0.1:8000/users/:id/ | DELETE | Delete user account by ID  | N/A | 204 | Authenticated User | PASS |
| http://127.0.0.1:8000/projects/    | GET | Returns all athlete projects  | N/A | 200 | Authenticated Admin | PASS |
| http://127.0.0.1:8000/projects/    | POST | Submit a Project for approval  | {"title", "description", "goal", "image"} | 201 | Authenticated User(Project_Owner) | PASS |
| http://127.0.0.1:8000/projects/:id/    | GET | Returns a specific project  | N/A | 200 | Authenticated User(Project_Owner or Admin) | PASS |
| http://127.0.0.1:8000/projects/:id/    | PUT | Edit/update Project   | {"title", "description", "image"}  | 200 | Authenticated User(Project_Owner or Admin) | PASS |
| http://127.0.0.1:8000/projects/:id/    | PUT | Edit/update Project   | {"goal"}  | 200 | Authenticated Admin | PASS |
| http://127.0.0.1:8000/projects/:id/    | DELETE | Delete specific Project | N/A | 204 | Authenticated Admin | PASS |
| http://127.0.0.1:8000/pledges/    | GET | Retrieve all Pledges for a Project | N/A  | 200 | Authenticated User(Project_Owner or Admin) | PASS |
| http://127.0.0.1:8000/pledges/:id/    | POST | Make a Pledge to a Project | {"amount", "anonymous"}   | 201 | Authenticated User | PASS |
| http://127.0.0.1:8000/pledges/:id/    | GET | Retrieve details of a specific pledge | N/A  | 200 | Authenticated User(Project_Owner or Admin) | PASS  |
| http://127.0.0.1:8000/pledges/:id/    | PUT | Update a pledge e.g. change amount | {"amount", "anonymous"}   | 200 | Authenticated User | PASS |
| http://127.0.0.1:8000/pledges/:id/    | DELETE | Delete a pledge | N/A | 204 | Authenticated Admin | PASS  |
| http://127.0.0.1:8000/users/:id/pledges/    | GET | Retrieve all pledges made by a user | N/A | 200 |  Authenticated User(Project_Owner or Admin) | PASS |
| http://127.0.0.1:8000/pledges/:id/ | GET | Filters and provides a list of Pledges who have contributed a certain amount | N/A | 200 | Authenticated User(Project_Owner or Admin) | PASS |

### DB Schema
Screenshot below but can also be referenced within ERD.drawio file
![Screenshot of DB Schema](https://github.com/BrooklinC/crowdfundproject_backend/blob/main/img/DB_SCHEMA.png)

### Screenshots of HTTP Requests
Local Screenshot of GET Request
![Screenshot of Local Get Request](https://github.com/BrooklinC/crowdfundproject_backend/blob/main/img/GET_REQUEST_LOCAL.png)

Local Screenshot of POST Request
![Screenshot of DB Schema](https://github.com/BrooklinC/crowdfundproject_backend/blob/main/img/POST_REQUEST_LOCAL.png)

Local Screenshot of Token Auth Request
![Screenshot of DB Schema](https://github.com/BrooklinC/crowdfundproject_backend/blob/main/img/TOKEN_LOCAL.png)

### Step-by-Step Instructions to Register a User
### 1. Register a New User
* Endpoint: POST /users/
* Action: Create a new user account.
* Required Data:
  - username: User's desired username (must be unique).
  - email: User's email address.
  - password: User's password.

### Steps:
1. Firstly, get excited because you've got a new user signing up - yay!
2. Send a POST request to /users/ with the required data in JSON format.
3. Ensure the Content-Type header is set to application/json.
4. On success, you'll receive a response confirming the user has been created.

### 2. Obtain an Authentication Token
* Endpoint: POST /api-token-auth/
* Action: Authenticate and receive a token for future requests.
* Required Data:
- username: Your username.
- password: Your password.

### Steps:
1. Send a POST request to /api-token-auth/ with your credentials in JSON format.
2. Ensure the Content-Type header is set to application/json.
3. On success, you'll receive an authentication token.
4. Save this token; you'll need it to authenticate future requests.

### 3. Create a New Project
* Endpoint: POST /projects/
* Action: Create a new project.
* Headers:
* Authorization: Include your token in the format Token your_auth_token_here.
* Content-Type: application/json
* Required Data:
- title: The project's title.
- description: A brief description.
- goal: Funding goal amount (e.g., 1000 for $1000).
- image: URL to an image representing the project.
- is_open: true if the project is open for pledges, false otherwise.
- date_created: (Optional) The creation date (usually auto-generated by the server).

### Steps:
1. Send a POST request to /projects/ with the project details in JSON format.
2. Include the Authorization header with your token.
3. Ensure the Content-Type header is set to application/json.
4. On success, you'll receive a response with the details of the newly created project.

```