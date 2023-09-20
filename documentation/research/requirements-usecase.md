# Report: Usecase 

## Actors:
- Citizen Developers
- Developers

## Requirements:
### Functional Requirements
1. *Authentication:* Sign in, Sign up, Log out
2. *Project Management:* Create and Edit project, Create and Edit Business Management, Search and Filter Project, DnD UI, Code-based component customization, Invite Collaborators, Test application, Deploy Application
3. *Data mapping:* Create Data Entities, Connect and to External Datasource, Read and Write from/to external Datasource 
4. *User management:* Change profile, Change password
**(lowest priority)**

### Non-functional Requirements
1. *Ease of use:*  The platform should be easy to use for both non-technical and technical users. The platform should have a drag-and-drop interface with various supported components, templates.
2. *Reliability:* 
Downtime must be ...
3. *Security:* The platform protects users data and users datasource from unauthorized access, modification or destruction: role-based access control, data encryption, and intrusion detection.
4. *Performance:* response time of system for each request is from ~200ms to ~2s

## Usecase Diagram

[Usecase Diagram](https://drive.google.com/file/d/1v7eiw8cQHYVr5MXE9QcOIMr9TU7ZAD1Y/view?usp=sharing)

### Usecase list
1. User signs up and signs in to use platform
2. User creates a project from scratch or from templates provided
3. User changes profile and passwords *(lowest priority)*
3. User invites collaborators to edit the project
5. User finds project by name or filters
3. User edits a project through dnd interface
4. User customizes components in edit view
5. User maps data and connects to variety of external data sources and make the queries
6. User creates and edits business logics then apply into the project
8. User creates savepoints (version) for the project *(Optional)*
8. User tests runnable application
7. From production stage, user be able to release a version of a product

## Usecase Scenario

### Sign in
| **Usecase**  | Sign-in |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User logs in into account created to use the platform |
| **Trigger** | User accesses the platform's link |
| **Pre-condition** | User has internet access <br/> Platform is working normally |
| **Post-condition** | User logs in successfully into platform |
| **Normal Flow** | 1. User clicks the third provider icon <br/> 2. System redirects to the authentication page of the third provider <br/> 3. User provides authentication information <br/> 4. Third provider checks information received and allow access <br/> System takes information for checking and redirect to main workspace page <br/> *Usecase ends*|
| **Alternative Flow** | None |
| **Exception Flow** | 3.1 System sends notification that the information provided is wrong or not existed <br/> 3.2 User chooses login again <br/> *Usecase continues at step1* <br/> 3.2.1 User cancels the sign in phase <br/> *Usecase ends*|

### Sign up
| **Usecase** | Sign up |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User creates account to use the platform|
| **Trigger** | At the login page, click button 'Sign up' <br/> Click the link sent in mail when user is invited to use|
| **Pre-condition** | User has internet access <br/> Platform is working normally|
| **Post-condition** |New account is created|
| **Normal Flow** | 1. User chooses to sign up by third party provider <br/> 2. System redirects to authentication page of third provider <br/> 3. User grants authentication to system <br/> 4. System takes the information received to create a account <br/> 5. System redirects to the main workspace of the account <br/> *Usecase ends*|
| **Alternative Flow** | None |
| **Exception Flow** | If user exits at any step, *Usecase ends*  |

### Log out 
| **Usecase**  | Log Out |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User logs out the current account from the platform|
| **Trigger** | User click the 'Log Out' on profile page/tab |
| **Pre-condition** |User logged in into the platform|
| **Post-condition** | System deletes user token/login from platform|
| **Normal Flow** |1. User click 'Log out' button <br/> 2. System shows modal for user to confirm action <br/> 3. User chooses 'Yes' <br/> 4. System deletes user token and redirects to sign in page <br/> *Usecase ends*|
| **Alternative Flow** | None |
| **Exception Flow** | 3.1 User chooses 'No' <br/> 3.2 System closes the modal <br/> *Usecase ends* |

### Create a project
| **Usecase**  | Create a new project in workspace |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User creates a new project to build an application |
| **Trigger** | In the workspace page, user clicks the 'New' button |
| **Pre-condition** | User logged in into platform <br/> User is in workspace page |
| **Post-condition** | A project is created and User can edit it |
| **Normal Flow** |1. User clicks 'New' button in the workspace <br/> 2. System shows available options for new project <br/> 3. User chooses 'Blank Project' or provided template. <br/> 4. System create project and setup the template then redirect to editor. <br/> *Usecase ends*|
| **Alternative Flow** | None |
| **Exception Flow** | At each step, if user choose 'Close' button, *Usecase ends*. |

### Edit a project
| **Usecase**  | Edit an existed project |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User edits the project to create application |
| **Trigger** | User goes to editor after create a new project <br/> User clicks the existed project in workspace |
| **Pre-condition** | User is the owner or has edit role of the project |
| **Post-condition** | Project is saved or updated new changes |
| **Normal Flow** | 1. User interacts with components provided through dnd interface <br/> 2. User clicks 'Save' <br/> 3. System saves the updated project then returns to workspace view. <br/> *Usecase ends*|
| **Alternative Flow** | 2.1 User doesn't click save button, but closes the edit view <br/> 2.2 System shows modal to make sure user's choice and whether to save the project <br/> 2.3 User chooses 'Save' button <br/> 2.4 System saves the updated project <br/> *Usecase ends*  <br/> <br/>At step 2.3: <br/> 2.3.1  User clicks 'Cancel' <br/> *Usecase continues at step 1* <br/> 2.3.a User clicks 'Don't save' <br/> 2.3.b System keeps the previous version of project <br/> *Usecase ends*|
| **Exception Flow** | None |

### Interact with components by Drag-n-Drop interface
| **Usecase**  | Interact Drag-n-Drop interface |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User uses drag-n-drop interface to create application or business process |
| **Trigger** | In edit view, user clicks the 'Component' tab  and click a component/business logic|
| **Pre-condition** | User has edit role and in edit view |
| **Post-condition** | Component/Business Logic is dropped in expected place |
| **Normal Flow** |1. User chooses an component in component tab <br/> 2. User drags the component into the main canvas then drops at the desired place <br/> 3. System creates the component at place that user dropped at and modifies canvas<br/> *Usecase ends*|
| **Alternative Flow** | 1.1 User chooses a created component in the main canvas <br/> *Usecase continues at step 2* <br/> <br/>At step 1.1: <br/> 1.2 User clicks 'Delete' button in Customize Tab <br/> 1.3 System deleted the component and modifies the canvas <br/> *Usecase continues at step 1* |
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

### Invite collaborators
| **Usecase**  | Invite collaborators |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User can invite collaborators to edit project |
| **Trigger** | User clicks 'Invite Collaborator' in settings project tab |
| **Pre-condition** | Collaborator has account of platform <br/> User is the owner of project |
| **Post-condition** | System sends collaborate invitation to whom user invited |
| **Normal Flow** | 1. User clicks 'invite collaborators' <br/> 2. System shows the input form <br/> 3. User inputs emails and their role and edit, view access <br/> 4. System setups and send invitation to emails <br/> *Usecase ends* |
| **Alternative Flow** | None |
| **Exception Flow** | If user exits at any step, *Usecase ends* |

### Search projects
| **Usecase**  | Search a project by name or filter |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User searches project in the workspace |
| **Trigger** | User clicks the search bar in the workspace |
| **Pre-condition** | User logged in into platform <br/> There are existing projects user created or has collaborator role |
| **Post-condition** | System shows projects that matches the information user provides |
| **Normal Flow** | 1. User clicks the search bar <br/> 2. User inputs the name of project <br/> 3. System shows list of projects that are exact match or near match <br/> *Usecase ends* |
| **Alternative Flow** | 1.2 User clicks the filter icon to the right of the search bar <br/> 1.3 System shows filter options form <br/> 1.3 User ticks the filter options <br/> *Usecase continues at step 3* |
| **Exception Flow** | At any steps, if user clicks outside the search bar <br/> *Usecase ends*|


### Create and Edit Business Process 
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

### Data mapping to External Datasource
| **Usecase**  | Mapping data entities to external datasource |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | Create data entities in project and mapping them to data from external datasource |
| **Trigger** | User clicks 'create and mapping entity' in the editor or in the main workspace|
| **Pre-condition** |User has datasource and can provide access config <br/> User is in a project or workspace|
| **Post-condition** | System can access to data source and can CRUD data to destination (data entities) based on authority allowed  |
| **Normal Flow** | 1. User creates entities and their relationships through a low-code UI of system <br/> 2. System shows a modal for user to choose datasource <br/> 3. User choose a datasource <br/> 4. System shows a form of datasouce config  <br/> 5. User provides config and grant access to system <br/>6. System alerts connect successfully and provide form for user to define datatype from external datasource <br/> 7. User defines datatype <br/> 8. System provides space for user to define mapping to entities <br/> 9. System does the mapping and saves <br/> *Usecase ends* |
| **Alternative Flow** | 5.1 System can't make connection <br/> 5.2 System returns to the config view <br/> *Usecase continues at step 5* |
| **Exception Flow** | None |

### Version control (Optional)
| **Usecase**  | User can control the version of the application |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User creates version in each stage of product creation process|
| **Trigger** | User click stage and version options  on tab when in project editor |
| **Pre-condition** | User is in project editor |
| **Post-condition** | User can create a version for  changes of project|
| **Normal Flow** | 1. User click stage and version options <br/> 2. System shows a form for user input <br/> 3. User chooses stage of application and click 'add new version' <br/> 4. User inputs name of version and description then click 'Add' <br/> 5. System creates a new version from savepoint of the version user is standing on <br/> *Usecase ends* |
| **Alternative Flow** | None |
| **Exception Flow** | None |

### Test application
| **Usecase**  | Test the flow of application |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User can test application when in staging stage |
| **Trigger** | User changes stage to staging on tab when in project editor|
| **Pre-condition** | User is in project editor <br/> User has testing plan |
| **Post-condition** | User can check if the application running appropriately|
| **Normal Flow** | 1. User changes stage to staging and chooses the version to test <br/> 2. System sets up environment and deploys the product in staging mode <br/> 3. User tests application as plan <br/> *Usecase ends* |
| **Alternative Flow** | None |
| **Exception Flow** | None |

### Deploy an application
| **Usecase**  | Generate an runnable application |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | From the development stage of the product, user can decide to deploy it |
| **Trigger** | Click the deploy button when user is in production stage |
| **Pre-condition** | User has a ready application stored in platform <br/> User is the owner of the application |
| **Post-condition** | System deploys the application on to server |
| **Normal Flow** | 1. In the view in production stage, user click 'deploy' button <br/> 2. System shows up a config view for user <br/> 3. User inputs version and description <br/> 4. System prepares the app and deploy it onto server <br/> 5. System opens the application in the new window <br/> *Usecase ends*|
| **Alternative Flow** | None |
| **Exception Flow** | None |