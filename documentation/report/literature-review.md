# Literature Review

***

- Review of existing low-code platforms and their features
- Exploration of related technologies and frameworks
- Analysis of similar projects or research in the field

***

## Martech Stack
### Definition
Martech Stack is a term used to describe the collection of technologies that marketers use to execute, analyze and improve their marketing across the customer lifecycle. The term "martech" is a combination of marketing and technology. Martech tools are used to automate or otherwise improve marketing processes, collect and analyze data, and provide various means of reaching and engaging with your target audience.

### Martech Stack Components
A martech stack is made up of a variety of tools and technologies that marketers use to execute, analyze and improve their marketing across the customer lifecycle. The components of a martech stack can be divided into 6 categories:
- Advertising & Promotion: tools that help you reach your target audience
- Content & Experience: tools that help you create and manage content
- Social & Relationships: tools that help you engage with your audience
- Commerce & Sales: tools that help you sell your products or services
- Data: tools that help you collect, analyze and mqanage data
- Management: tools that help you manage your marketing operations

A sample martech stack can be seen in the following image:
![martech-stack](/images/martech-stack.png)

Here are some key components and features typically found in a marketing automation platform:

- Customer Relationship Management (CRM): A marketing automation platform often integrates with a CRM system to centralize customer data, including contact information, purchase history, and interactions. This data enables marketers to create personalized and targeted campaigns.

- Lead Management: Marketing automation platforms help businesses capture, track, and manage leads throughout the customer journey. Leads can be segmented based on various criteria such as demographics, behavior, or engagement level, allowing marketers to deliver relevant content and nurture leads until they are ready for sales.

- Email Marketing Automation: These platforms provide tools for designing, scheduling, and sending automated email campaigns. Marketers can create personalized email workflows triggered by specific actions or events, such as subscribing to a newsletter, abandoning a shopping cart, or completing a purchase.

- Campaign Management: Marketing automation platforms offer campaign management features to plan, create, and execute multi-channel marketing campaigns. This includes managing social media posts, paid advertising campaigns, landing pages, and tracking campaign performance.

- Personalization and Segmentation: These platforms enable marketers to deliver personalized content to specific audience segments. They use data and behavior tracking to tailor messages, offers, and recommendations based on individual preferences and past interactions.

- Analytics and Reporting: Marketing automation platforms provide comprehensive analytics and reporting capabilities to measure the effectiveness of marketing campaigns. Marketers can track and analyze key performance indicators (KPIs) such as email open rates, click-through rates, conversion rates, and ROI to optimize their strategies.
8
- Workflow Automation: Automation workflows are a core feature of marketing automation platforms. Marketers can create predefined sequences of actions and triggers based on specific conditions or events. These workflows automate repetitive tasks, such as sending follow-up emails, assigning leads to sales representatives, or updating customer records. 

### Existing Low-code Development Platforms Comparison
Low-code Developing is slowly becoming a thing in business environment. And to keep up with the demand, many low-code development platforms have been provided for the business users with a large variety of usage and pricing. Yet, we would like to introduce 3 platforms that we consider the most notable ones. We are going to categorize them into 3 groups:
- Open-source
- Proprietary, free-to-use
- Proprietary, paid

### Open-source
Our candidate for this category is going to be **[ToolJet](https://github.com/ToolJet/ToolJet)**. ToolJet is an open-source low-code framework to build and deploy internal tools with minimal engineering effort. ToolJet's drag and drop frontend builder allows you to create complex, responsive frontends within minutes. Additionally, you can integrate various data sources, including databases like PostgreSQL, MongoDB, and Elasticsearch; API endpoints with OpenAPI spec and OAuth2 support; SaaS tools such as Stripe, Slack, Google Sheets, Airtable, and Notion; as well as object storage services like S3, GCS, and Minio, to fetch and write data.

![ToolJet Demo](/images/tooljet.png)

#### Pros
- Visual Drag-n-Drop App Builder
  - ToolJet provides a drag-n-drop app builder with a variety of prebuilt resizable components that are ready to use. Each component has its own event handler to trigger an action which is also predefined in the application.
- Database:
  - With ToolJet, you can either use its own ToolJet Database or integrate with an existing data sources. ToolJet can support integration with over 40 different data sources, including SQL, MongoDB, FireStore, InfluxDB, MariaDB or even RESTful API.
- Collaboration:
  - An app can be edited and customized by multiple users simultaneously with ToolJet's Multiplayer editing.
- Version Control:
  - Users can manage multiple application versions with a structured release cycle.
- Customization:
  - If prebuilt scripts and components are not sufficent, users can implement their own JavaScript and Python code into the application.
#### Cons
- Confusing User Experience:
  - Although the drag-n-drop interface provides a decent amount of prebuilt components, interacting with them is not a good experience for newcomers. Moving a component around the canvas can easily trigger an inner component of the component itself. The user will also has no clue how the final page will look like since the canvas only contains components. There is no border or boundary for the user to identify where the component is going to get positioned on the product.
  - Components can overlap each other and there is no way to get a component to get on top. For example, if a button component is placed inside of a table component, the moment you hover on the table, it will overlap the button and you will not be able to ever select the button unless you move a table to another position. This might be a feature indicating that components should not overlap each other but ToolJet could have done it in a better way.
- High loading time for previewing:
  - It took around 1 to 2 seconds in order to load the preview for the application, which is fine but the way the preview loaded is confusing since initially what you get is a blank page with a page navigation column on the left. There is no indication that the page is still loading and might give the users the feeling of something has gone wrong during the loading process.
- Lack of workflow management:
  - Any features related to workflow are nowhere to be found in the main interface. Despite the fact that ToolJet does have a workflow editor, it is still in a beta phase and only available for paid plans.

### Proprietary, free-to-use
For the next category which is a platform that is proprietary but free to use, we are choosing **[Google AppSheet](https://about.appsheet.com/home/)**, a low-code / no-code platform to build apps and automate work.

![Google Appsheet](/images/appsheet.png)

#### Pros
- Friendly User Interface / User Experience:
  - So far, Google Appsheet has the greatest UX of all. All menus and items are placed scientifically so that it gives the user an ease to get started. In addition, the UI is following the philosophy of Material You design from Google just like many other Google apps. This gives a responsive feeling while you are interacting with the platform.
- Application Builder:
  - Google Appsheet provides us previews of the application for many types of device, ranging from Mobile to Tablet and even Desktop, without having to make changes for each one. Google Appsheet also has some prebuilt components to add in the applications with a high ability of customization.
- Database Integration:
  - Google Appsheet has a prebuilt database and is ready to use, including another platform to directly edit that database just like Microsoft Excel. Beside, Google Appsheet supports integrate data from other sources such as Google Sheets, Google Drive Documents, Cloud Database, etc.
- Workflow Automation:
  - Users can define a set of custom processes in Google Appsheet with its Automation page. For each process, Google Appsheet also provides users with some predefined actions such as sending notifications (email, SMS), calling webhook, calling a script from Google AppScript, etc.

#### Cons
- Limited choices of components:
  - One drawback of this platform is its lack of prebuilt components comparing to other platforms. In addition, these components are not drag-n-drop. Therefore you cannot freely set positions of these components. Beside, you can only choose one component per page, which is called a View Type.
- Limited choices of actions for app components:

- Limited choices of workflow actions:
  - Each step of a process is only given a small amount of actions. If you want to extends the functionality of the automation process, users would have to rely on making a custom Google AppScript script, which is a JavaScript-lookalike scriting language. This really defeats the purpose of a no-code platform as Google has stated.
  - Beside, the workflow system in Google AppSheet is pretty much limited in which they can only support simple workflow. There is no branching support in the workflow or so.

### Proprietary, paid
Due to our financial limitation, we could not really have an insight in platforms that need to be paid in order to start using. However, we end up got suggested with a free to develop platform which is called **[Bubble.io](https://bubble.io/)**. The only catch is that to deploy the application, we need a paid account. Since our scope is focus on researching the platform main functionality, we do not need to deploy anything.

![Bubble.io](/images/bubbleio.png)

#### Pros
- Friendly drag-n-drop interface:
  - Bubble.io provides an easy to approach visual editor for application GUI. It also includes a large variety of prebuilt elements and an element hierarchy list. 
- Wide variety of workflow actions:
  - When talking about workflow handling, Bubble.io really stands out with its large amount of predefined actions for workflow handling, ranging from account management to data analytics. In addition, the UX on the workflow dashboard is better comparing to other platforms.
- Highly configurable application style:
  - Another Bubble.io's key point is about its ability to customize the interface and styles of the application UI. For each prebuilt components, Bubble.io provides a separate setting panel in which users and freely edit the component. 
- Localization support:
  - Many languages have already been supported on Bubble.io and can be applied to the application itself. There also exists a dashboard where you can edit custom error messages.
#### Cons
- Limited to little connection to external data sources:
  - One drawback of the platform is its inability to connect to external data sources. Every database action must be performed under the database service given by the platform.

### Platform Comparison
To summarize, we would like to compare the three mentioned above platforms in a table. And with that in mind, we can choose which function we are implementing in our application.

|                                             | ToolJet | Google AppSheet | Bubble.io |
| ------------------------------------------- | :-----: | :-------------: | :-------: |
| Drag-n-drop Visual Editor                   |    ✔️    |        ❌        |     ✔️     |
| DBMS                                        |    ✔️    |        ✔️        |     ✔️     |
| Ability to connect to external data sources |    ✔️    |        ✔️        |     ❌     |
| Collaboration                               |    ✔️    |        ❌        |     ✔️     |
| Workflow manager                            |    ❌    |        ✔️        |     ✔️     |
| Customizable components                     |    ❌    |        ❌        |     ✔️     |
| Localization                                |    ❌    |        ❌        |     ✔️     |
| Cross-platform support                      |    ✔️    |        ✔️        |     ❌     |