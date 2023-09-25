# Requirement Analysis

***

- Identification and documentation of functional and non-functional requirements
- Use cases and user stories for the low-code platform
- Discussion of expectations and limitations of the project

***

# Actor
- Developer: include citizen developers and technical developers who create application by platform
- *Example*: developers, system engineers, business employees in different departments like sales, marketing, etc.   
- External database, CMS
- Third-party Provider
# Requirements
## Functional requirements
### For Developer (User)

The platform provides lowcode UI or drag-n-drop interface for users to interact with when editing or customizing

**Authentication**
- Sign up by third-party provider
- Sign in by third-party provider

**Manage Project**
- Create a project to generate an application from blank or templates
- Edit Project
- Customize provided components by lowcode UI or Js code
- Search components
- Invite a collaborator to join editing project
- Find Project by name or filter projects created
- Delete projects 

**Manage Datasource**
- Doing CRUD with table (database) provided by platform
- Connect to external datasource to create data table and map data

**Deploy Application**
- Create versions of projects and applications by savepoints functionality 
- Using preview mode to display and check their applications and workflows
- Deploy an application onto server from projects

**Manage Business Process**
- Create a business process with business logics
- Edit an existing business process
- Add business process to application
- Create a business logic
- Customize a provided business logic

**Optional - Functionality can be considered updating in future**
- Be supported stages of project development: *Develop, Staging, Production*
- Manage account information: change password, profile, etc.
- Debug an application - track execution of application
- Create project templates
- Create business process templates
- Track changes to the projects over time
## Non-functional requirements
| Non-Requirements | Details | Metrics |
| :---- | :---- | :---- |
| Performance| 	The platform must be able to handle a large number of concurrent users without any performance degradation | Response time < 2 second for 100 concurrent users |
| Reliability | The downtime percentage of platform should remain low | The downtime percentage remain under 2% and the probability encountering errors of users is under 5% a month |
| Security | Platform protects user data and datasource from unauthorized access, modification, destruction  | Role-based access control, data encryption, and auditing. |
| Localization| Platform supports multi-language | Vietnamese and English |
| Usability | Easy to use, Good UI | Platform allows non-technical users to get up and running with under 30 minutes learning   |

# Usecase
## Usecase Diagram
[Usecase Diagram](https://drive.google.com/file/d/1v7eiw8cQHYVr5MXE9QcOIMr9TU7ZAD1Y/view?usp=sharing)
## Usecase Scenario
### Sign in
| **Usecase**  | Sign-in |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User logs in into account created to use the platform |
| **Trigger** | User accesses the platform's link |
| **Pre-condition** | User has internet access <br/> Platform is working normally |
| **Post-condition** | User logs in successfully into platform |
| **Normal Flow** | 1. User clicks the third provider icon <br/> 2. System redirects to the authentication page of the third provider <br/> 3. User provides authentication information <br/> 4. Third provider checks information received and allow access <br/> 5. System takes information for checking and redirect to main workspace page <br/> *Usecase ends*|
| **Alternative Flow** | None |
| **Exception Flow** | 3.1 System sends notification that the information provided is wrong or not existed <br/> 3.2 User chooses login again <br/> *Usecase continues at step1* <br/> 3.2.1 User cancels the sign in phase <br/> *Usecase ends*|

### Edit a project
| **Usecase**  | Edit an existed project |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User edits the project to create application |
| **Trigger** | User goes to editor after create a new project <br/> User clicks the existed project in workspace |
| **Pre-condition** | User is the owner or has edit role of the project |
| **Post-condition** | Project is saved or updated new changes |
| **Normal Flow** | 1. User interacts with components  and the main canvas: drag-n-drop, customize components, etc. <br/> 2. User clicks 'Save' <br/> 3. System saves the updated project then returns to workspace view. <br/> *Usecase ends*|
| **Alternative Flow** | 2.1 User doesn't click save button, but closes the edit view <br/> 2.2 System shows modal to make sure user's choice and whether to save the project <br/> 2.3 User chooses 'Save' button <br/> 2.4 System saves the updated project <br/> *Usecase ends*  <br/> <br/>At step 2.3: <br/> 2.3.1  User clicks 'Cancel' <br/> *Usecase continues at step 1* <br/> 2.3.a User clicks 'Don't save' <br/> 2.3.b System keeps the previous version of project <br/> *Usecase ends*|
| **Exception Flow** | None |

### Customize a component
| **Usecase**  | Customize a component in project |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User customizes the provided component to use in project |
| **Trigger** | User clicks a component in the canvas |
| **Pre-condition** | User is in editor of a project |
| **Post-condition** | Component is updated in project based on user config |
| **Normal Flow** | 1. User chooses what to config in customize tab: color, name, event, ... <br/> 2. System changes to config view of each type <br/> 3. User customizes the component through a click-based UI and click 'Save' <br/> 4. System updates the component UI based on configuration and modifies the main canvas <br/> *Usecase ends*|
| **Alternative Flow** | 3.1 User can use code-based config by JS, ... and click 'Save'<br/> *Usecase continues at step 4* |
| **Exception Flow** | None |

### Create and Edit business process

| **Usecase**  | Create and Edit a business process to apply in application |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User defines and applies business process into the product |
| **Trigger** | User clicks 'Add business process' in Customize Tab when customize component <br/> User clicks a business process in business customize tab in workspace |
| **Pre-condition** | User logged in and in customize view or in main workspace |
| **Post-condition** | Business process is created and added by system |
| **Normal Flow** | 1. User clicks a blank business process or an existing business process <br/> 2. System brings user to another drag-n-drop edit view. <br/> 3. User chooses provided components/node about business logic and drag-n-drop into the dashboard <br/> 4. User click 'save' button <br/>5. System updates and saves the changes <br/> *Usecase ends* |
| **Alternative Flow** | 5.1 If user triggers in customize view, system adds the business process to targeted component. <br/> *Usecase ends* <br/> <br/> At step 4: <br/> 4.1 User doesn't click save button, but closes the edit view <br/> 4.2 System shows modal to make sure user's choice and whether to save the business project <br/> 4.3 User chooses 'Save' button <br/> 4.4 System saves the updated business process <br/> *Usecase ends*  <br/> <br/>At step 4.3: <br/> 4.3.1  User clicks 'Cancel' <br/> *Usecase continues at step 3* <br/> 4.3.a User clicks 'Don't save' <br/> 4.3.b System keeps the previous version of project <br/> *Usecase ends* |
| **Exception Flow** | None |

### Create data table

| **Usecase**  | Create data table |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User creates data model or data table for use |
| **Trigger** | User clicks "Add Datasource" in the panel |
| **Pre-condition** | User has logged in into platform |
| **Post-condition** | System can access to data source and can CRUD data to destination (data entities) based on authority allowed |
| **Normal Flow** | 1. User click "Database" in the right toolbar then click "Add" button <br/> 2. System shows the modal for user to choose <br/> 3. User chooses the database and provides configuration about access and authority <br/> 4. System connects to database and retrieve data <br/> 5. System renders the data into table views with column, options box that user can interact with to view or edit model or CRUD request <br/> *Usecase ends* |
| **Alternative Flow** | None |
| **Exception Flow** | None |

### Deploy an application

| **Usecase**  | Generate an runnable application |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | From the preview mode of the product, user can decide to deploy it |
| **Trigger** | Click the deploy button when user is in preview mode |
| **Pre-condition** | User has a ready application stored in platform <br/> User is the owner of the application |
| **Post-condition** | System deploys the application on to server |
| **Normal Flow** | 1. In the view in preview mode, user click 'deploy' button <br/> 2. System shows up a config view for user <br/> 3. User inputs description <br/> 4. System prepares the app and deploy it onto server <br/> 5. System opens the application in the new window <br/> *Usecase ends*|
| **Alternative Flow** | None |
| **Exception Flow** | None |