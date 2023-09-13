# Actors
- Citizen developer (non-technical developer)
- Developer
# Requirements
## Functional Requirements
1. Users should be able to create and edit web applications using a visual drag and drop interface.

2. Users should be able to define the business logic of their application using a visual interface.

3. Code-based customization options should be available for each element in the visual interface.

4. Connection to external data sources should be possible.

5. Users should be able to generate code from the platform to produce a runnable application.

6. CI/CD should be possible from the platform.

7. Testing of the application should be possible from the platform.

---
8. *Sign in by username, email and by third providers* ??
## Non-functional Requirements
1. *Ease of use:*  The platform should be easy to use for both non-technical and technical users. The platform should have a drag-and-drop interface with various supported components, templates.
2. *Reliability:* The platform should be reliable and available 24/7: load balancing, etc.
3. *Security:* The platform protects users data and users datasource from unauthorized access, modification or destruction: role-based access control, data encryption, and intrusion detection.
4. *Scalability*: The platform should be able to scale to handle increasing numbers of users and workloads

# Use-case
## Diagram
## Use-case list
### For User 
**Scenario Available**
1. User can sign-up/sign-in into platform by username,password or by third provider.
2. User can create a project from scratch or from templates provided
3. User can edit a project through dnd interface
4. User can customize components in edit view
5. User can connect to variety of external data sources and make the queries

**Not Yet from Requirement to Scenario**
- Create and edit business logics
- Generate runnable product
- CI/CD should be possible from the platform.
- Testing of the application should be possible from the platform.
## Use-case Scenario
### Sign-in
| **Usecase**  | Sign-in |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User logs in into account created to use the platform |
| **Trigger** | User accesses the platform's link |
| **Pre-condition** | User has internet access <br/> Platform is working normally |
| **Post-condition** | User logs in successfully into platform |
| **Normal Flow** | 1. User enters username and password and click button 'Sign in' <br/> 2. System checks the information provided <br/> 3. System sends notification informing successfully login the redirect to workspace page of user <br/> 4. Usecase ends   |
| **Alternative Flow** | 1.1 User don't choose sign in by username and password but click button sign in by the third provider <br/> 1.2 System redirects to the authentication page of the third provider <br/> 1.3 User provides authentication information <br/> 1.4 Third provider checks information provided and allow access <br/> *Usecase continues at step 4* |
| **Exception Flow** | 3.1 System sends notification that the information provided is wrong or not existed <br/> 3.2 User chooses login again <br/> *Usecase continues at step1* <br/>3.2.1 User chooses forgot password <br/> *Usecase continues at ...*  <br/> 3.2.2 User cancels the sign in phase <br/> *Usecase ends*|

### Create New Project
| **Usecase**  | Create new Project |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User creates a new project |
| **Trigger** | When in the workspace, click the 'New' button then choose create new project |
| **Pre-condition** | User signs in successfully and  |
| **Post-condition** | User creates a project and go to edit project page |
| **Normal Flow** |1. User clicks 'New' button in the workspace and system shows available options <br/> 2. User choose 'Blank Project'. <br/> 3. System create project and setup the template then redirect to editor.|
| **Alternative Flow** |2.1 User can change to template tab to change a template provided. <br/> *Usecase continue at step 3*|
| **Exception Flow** |At each step, if user choose 'Close' button, *usecase ends*.|
### Edit Project
| **Usecase**  | Edit a project in user workspace |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** |User edits project to render the application|
| **Trigger** | User chooses create new project or selects project that has been saved in the workspace|
| **Pre-condition** |User is an owner or a collaborators of the project (has edit role)|
| **Post-condition** |Project is updated and saved|
| **Normal Flow** |1. User interacts with components provided through dnd interface <br/> 2. User clicks 'Save' <br/> 3. System saves the updated project then returns to step 1. |
| **Alternative Flow** |2.1 User doesn't click save button, but closes the edit view <br/> 2.2 System shows modal to make sure user's choice. <br/> 2.3 User clicks 'Save the changes' <br/> 2.4 System saves the updated project. <br/> *Usecase ends* <br/> 2.3.1 User clicks 'Cancel' <br/> *Usecase continue at step 1* <br/> 2.3.2 User clicks 'Don't save' <br/> 2.3.3 System keep the previous version of project <br/> *Usecase ends* |
| **Exception Flow** |None|

---
| **Usecase**  | Interact with Dnd Interface |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** |User uses dnd interface to complete their project|
| **Trigger** | At edit view, User click at 'Component' tab.|
| **Pre-condition** |User is editing a project|
| **Post-condition** |Component is placed in edit view|
| **Normal Flow** |1. User choose 'component' and choose what type of component <br/> 2. User drags the component into the main view then drops at the right place <br/> 3. System modify the component at place that user dropped at|
| **Alternative Flow** |1.1 User clicks the existed component in the main view <br/> 1.2 User drags the component <br/> *Usecase continue at step 2* <br/> 1.2.1 User clicks delete the component <br/> *Usecase continues at step 3*
| **Exception Flow** |*At each step, user closes the edit view, return to Usecase Edit Project - step 2.2*|

### Customize the Component
| **Usecase**  | Customize the Component in edit view |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | In editing phase, user can customize the component provided that used in the production |
| **Trigger** | User clicks the component that is dnd in the main view |
| **Pre-condition** | User is in the edit view |
| **Post-condition** | Component is updated based on config user provides |
| **Normal Flow** | 1. User chooses config the component: name, UI, event, ... <br/> 2. System changes to config view <br/> 3. User customize the components through a click-based UI and click 'Save' <br/> 4. System updates the component UI based on configuration|
| **Alternative Flow** |3.1 User can use code-based config by JS, ... and click 'Save'<br/> *Usecase continues at step 4*|
| **Exception Flow** | None |
### Connect to external Data Source
| **Usecase**  | Connect to external data source |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** | User can provide config, auth then platform provides connection to data source|
| **Trigger** | User clicks 'add data source' in the project|
| **Pre-condition** | User has datasource and can provide access config <br/> User is in a project or workspace. |
| **Post-condition** | Platform can access to data source and can CRUD based on authority allowed |
| **Normal Flow** |1. User chooses type of datasource and specific datasource <br/> 2. System provides the config form based on the chosen datasource. 3. User inputs the config <br/> 4. System uses the configs request and make connection to datasource then redirect to query config view <br/> 5. User configs the query then click 'Save' <br/> 6. System saves the connection and queries |
| **Alternative Flow** |4.1 System can't make connection <br/> 4.2 System returns to the config view <br/> *Usecase continues at step 3* <br/> 3.1 (case: return from step 4.2) <br/> 3.2 User chooses 'Back' <br/> 3.3 System return to datasource choose view <br/> *Usecase continues at step 1*|
| **Exception Flow** | None |
### Create and Edit Business Logic
| **Usecase**  | Sign-in |
|:---|:---|
| **Actor** | User (Nontechnical or technical user) |
| **Description** ||
| **Trigger** ||
| **Pre-condition** ||
| **Post-condition** ||
| **Normal Flow** ||
| **Alternative Flow** ||
| **Exception Flow** ||