# crowdfundproject_backend

# Project Title
__The Golden Goose__

## Planning:
### Concept/Name
The Golden Goose is a crowdfunding platform designed specifically to support future Olympians and Paralympians by helping them fund their training, equipment and competition expenses.

### Intended Audience/User Stories
**Intended Audience:**

**Athlete Creators:** Individual Athletes can create detailed profiles and campaigns showcasing their goals, achievements and funding needs. 

**Pledges:** People interested in supporting individual athletes directly and transparently.

**User Stories:**
*As an Athete Creator*, I want to be able to setup my project with my profile, goals and funding needs to feature on The Golden Goose and elicit potential pledgers. 

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

### API Spec
| URL | HTTP Method | Purpose | Purpose | Request Body | Success Response Code | Authentication/Authorisation |
| ---| ----------- | ------- | ------- | ------------ | --------------------- | ---------------------------- |
| http://127.0.0.1:8000/users/ | POST        | Register a New User | ------- | ------------ | --------------------- | ---------------------------- |
| http://127.0.0.1:8000/users/     | GET         | Retrieve a list of users        |         |              |                       |                              |
| http://127.0.0.1:8000/users/<pk>/     |             | Retrieve user profile by ID    |         |              |                       |                              |
| http://127.0.0.1:8000/users/<pk>/     |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/users/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/projects/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/projects/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/projects/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/projects/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/projects/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/projects/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/pledges/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/pledges/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/pledges/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/pledges/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/pledges/<pk>/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/users/<pk>/pledges/    |             |         |         |              |                       |                              |
| http://127.0.0.1:8000/pledges/<pk>/    |             |         |         |              |                       |                              |
|     |             |         |         |              |                       |                              |

### API Spec 2

+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| URL                                       | HTTP Method | Status | Purpose                                                                                                | Request Body                                                     | Expected Response Code | Authentication / Authorisation         |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/users/              | POST        | PASS   | Register a new user                                                                                    | {"username",   "email", "password"}                              | 201                    | Public                                 |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/users/              | GET         | PASS   | Retrieve a list of users                                                                               | N/A                                                              | 200                    | Authenticated Users (Admin)            |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/users/<pk>/         | GET         | PASS   | Retrieve user profile by ID                                                                            | N/A                                                              | 200                    | Authenticated Users (User or Admin)    |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/users/<pk>/         | PUT         | PASS   | Update user profile by ID                                                                              | {"username",   "email", "first_name", "last_name",   "password"} | 200                    | Authenticated Users (User or Admin)    |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/users/<pk>/         | DELETE      | PASS   | Delete user account by ID                                                                              | N/A                                                              | 200                    | Authenticated Users (User)             |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/projects/           | GET         | PASS   | Returns all athlete projects                                                                           | N/A                                                              | 200                    | Public                                 |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/projects/           | POST        | PASS   | Submit a Project for approval                                                                          | {"title",   "description", "goal", "image"}                      | 201                    | Authenticated Users (Owner)            |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/projects/<pk>/      | GET         | PASS   | Returns a specific project                                                                             | N/A                                                              | 200                    | N/A                                    |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/projects/<pk>/      | PUT         | PASS   | Edit/Update Project                                                                                    | {"title",   "description", "image"}                              | 200                    | Authenticated Users (Owner)            |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/projects/<pk>/      | PUT         | FAIL   | Edit/Update Project                                                                                    | {"goal"}                                                         | 200                    | Authenticated Users (Admin)            |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/projects/<pk>/      | DELETE      | PASS   | Deletes specific Project                                                                               | N/A                                                              | 200                    | Authenticated Users (Admin)            |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/pledges/            | GET         | PASS   | Retrieve all Pledges for a project                                                                     | N/A                                                              | 200                    | Authenticated Users (Owner)            |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/pledges/<pk>/       | POST        | PASS   | Make a pledge to a project                                                                             | {"amount",   "anonymous")                                        | 201                    | Authenticated Users (Pledges)          |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/pledges/<pk>/       | GET         | PASS   | Retrieve details of a specific pledge                                                                  | N/A                                                              | 200                    | Authenticated Users (Owner or Pledge)  |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/pledges/<pk>/       | PUT         | FAIL   | Update a pledge (e.g. Change amount)                                                                   | {"amount",   "anonymous")                                        | 200                    | Authenticated Users (Pledges)          |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/pledges/<pk>/       | DELETE      | FAIL   | Delete a pledge                                                                                        | N/A                                                              | 200                    | Authenticated Users (User)             |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/users/<pk>/pledges/ | GET         | PASS   | Retrieve all pledges made by a user                                                                    | N/A                                                              | 200                    | Authenticated Users (Pledges)          |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+
| http://127.0.0.1:8000/pledges/<pk>/       | GET         | FAIL   | Filters and provides a list of   Pledges who have contributed a certain amount (Project ID and Amount) | N/A                                                              | 200                    | Authenticated Users (Owner or   Admin) |
+-------------------------------------------+-------------+--------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------+------------------------+----------------------------------------+

### DB Schema
![]( {{ ./relative/path/to/your/schema/image.png }} )
```

An example API spec:  
![](./img/table.png)

### Step-by-Step Instructions to Register a User
    Step 1:
    Step 2:
    Step 3:
    Step 4: