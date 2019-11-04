# Ideas to deploy for classroom
- Create user stories in Mendix developer portal
```
Add your First User Story
Time for you to try! Add one of the user stories we defined earlier. Use the following details:

User story: As an administrator, I want to be able to manage my data, so that I can make changes at any time.

Story type: Feature

Story points: Add an estimate. How much effort do you think it will take?

Description: How would you describe this user story so that your team understands what it’s about?

We will need that user story for the next part of the training, so make sure you add it to your backlog!
```
- Creating user stories in Excel and import on Mendix
![Excel User Stories](/images/excel_user_stories.png "Excel User Stories")

# Learning Path - Rapid Developer (Analyst)

# Errors
## After deleting Stories
Resolved through log-out and log-in.

# Mendix

The goal of this project is to learn low-code app development with Mendix and find a solution to deliver it in a classroom setting for courses in City University of Seattle.

## Basics
- Development Process
- Building Pages
- Domain Model
- Microflows
- Data Validation and Consistency
- Application Security

## Interface

![Interface](/images/interface.png "Interface")
1. Page Editor
2. Menu
  - Page editor: It allows you to define the end-user interface of a Mendix application. You can use that to navigate to the various pages of your app or create new ones.

  - Domain model: It is a data model which describes the information in your app in an abstract way. It allows you to quickly check what data is there and how it is connected.


![Domain Model](/images/domain_model.png "Domain Model")

  - Microflow editor: Microflows are a visual way of expressing custom logic in your app. When there is no button to do an action that you want to do in your app, then you can create your own!

![Interface](/images/microflow.png "Interface")
  - Navigation: It shows a configured menu of your app in a form of a tree. You can create items and sub-items so that your users can find their way in the app easily.

  - Search: A quick way to find elements in your app.

  - Theme customizer: Here you can adjust colors, upload a logo, change the text style, and make your app look the way you want.

  - Settings: It contains information on Mendix App Store widgets and local widgets in your app.
3. Breadcrumbs show which element is selected in the Editor.
![Navigation Layout](/images/navigation_layout.png "Navigation Layout")

4. Toolbox, Properties, Buzz
5. Preview
6. Navigation Menu

Open the Navigation Document (which you can access by using the navigation menu on the left side of Mendix Studio).

You can add main navigation items and sub-items:

![Navigation Menu](/images/nav_menu.png "Navigation Menu")

# Concepts
## Mendix Lifecycle
1. Capture
  - Buzz
  - User Stories
  - Wireframes
2. Develop
  - Sprint Planning
3. Deploy
4. Operate
## Project Roles
Each Scrum process needs a couple of vital roles to be successful: the Product Owner, the Scrum Master, and the Development Team. Altogether, these roles comprise the Scrum Team.
![Project Roles](/images/project_roles.png "Project Roles")
## Project - Methodology Agile
![Agile Process](/images/agile_process.png "Agile Process")

## User Stories
Here are three things to think of when creating a user story:

Who is my app’s end-user?  `<user type>`

What does the end-user need to do? `<business value>`

How can I help them do that? `<what>`

Then, you can use this simple user story template:
```
As a <user type>, I want <what>, so that <business value>.
```
Examples:
- As an administrator, I want to be able to add a new training, so that I can keep my trainings up-to-date.
  - Story type: Feature
  - Story points: 5
  - Description:
```
I need to be able to view and manage all my:
- Courses
- Locations
- Teachers

When I am at the office I use my desktop, but when I am traveling for work. I mostly use my tablet and mobile phone. Therefore, It's really important for me to be able to manage all of the above data from desktop, tablet, or mobile.
```
- As an administrator, I want to be able to edit a training, so that I can keep my trainings up-to-date.

- As a teacher, I need to be able to view the email address of each participant, so that I can send them their certificates of participation.
### Story Points
Represent the effort it will take to finish that user story.
### Tasks
You can further break down the work that needs to be done for the user story into (sub-) tasks.

![Story and Tasks](/images/stories.png "Story and Tasks")

## Sprint
### Sprint Status
Shows you how much you have progressed towards the goal of your Sprint

![Sprint Status](/images/sprint_status.png "Sprint Status")
### Burndown Chart
It presents user stories and tasks, and also takes into account the effort needed to finish each user story.

![Burndown Chart](/images/burndown_chart.png "Burndown Chart")
### Release Plan
 It can help you set priorities and give you a better estimate of what needs to be done when!

![Release Plan](/images/release_plan.png "Release Plan")

## Wireframing
![Wireframing](/images/agile_process.png "Wireframing")

## Wireframing the User Story
### As an administrator, I want to be able to easily access and manage my data, so I can run my company more efficiently.
Completing this user story would involve the following tasks:
1. Have a homepage that gives access to pages where information can be seen.
2. Adjust the homepage layout to accommodate for the buttons to be created.
3. Add the buttons.
4. Add the pages to which the buttons will link.
5. Link the buttons to these pages that show the information in the system.
![Wireframe Pages](/images/wireframe_pages.png "Wireframe Pages")
![Wireframe Pages Detailed](/images/wireframe_pages_detailed.png "Wireframe Pages Detailed")

## Layout Grid
The layout grid is a widget that gives structure to your pages. It contains one or more rows, and each row contains 1–4 columns (in the Mendix Studio Pro, you can expand that to be twelve columns). Each column has a weight (a number from 1 to 12), and the total of the weights of the columns in a row must always add up to 12 (in the example below: one column with weight 12; two columns with weight 6; one of 3 and one of 9).
## Containers and Widgets
Once you have created the page structure (the layout), you start building the content of the page by adding different kinds of widgets. These can be, for example, text widgets to display text or button widgets.

You can place these widgets inside containers. There are a few reasons to do this:

- You can group the widgets. This will allow you to move them all at once (if needed), or put a border around them to group them visually for your end-user. You can also group them to hide all of them at once.

- You can add multiple widgets in a container to give them consistent styling.

- You can use the container to create spacing and alignment in pages (for example, to align a group of buttons to the right side of the page, or to create spacing around a button).

A container is also considered a widget.

## Entities and Attributes
Before showing data in your app, you first need to understand two basic principles:

Entities - To show data in your app, you need to connect the list view to an entity. An example of an entity for the LearnNow app would be Course. The entity will be filled with attributes.

Attributes - Attributes determine what kind of information regarding the courses you can see and add (for example, a title and description). Each attribute has a data type. This property defines the type of data that can be stored in the attribute, just like you format the cells of an Excel sheet.

In other words: An Entity is the Data that is displayed, and the attribute defines the format of that Data.

The following Attribute types are available, each with their possible values:
![Attribute Types](/images/attribute_types.png "Attribute Types")
### Example
Take a look at the following image of a jar of strawberry jam. The jar would be the entity in this example, but can you think of a couple of attributes and their types for this jar?

![Attribute Example](/images/attribute_example.png "Attribute Example")
### Define Attributes
![Define Attributes](/images/define_attributes.png "Define Attributes")

## Objects
An Object is a single instance of an Entity, consisting of Attributes. You can create multiple Objects based on one entity. These Objects can be stored in the database. You can see the Entity and its Attributes combined as a blueprint of the information you can add to your app. So, each Course in the system is an Object, and when you create a new Course, you create a new Object of the type (entity) Course.

If you think back to the jar example, the Entity and Attributes are like the blueprint of the jar, handed to the manufacturer so he knows what the jar should look like when he makes it. Once he starts producing the jars, each jar that is created is an Object. The database would be like a shelf where you store all the created jars.

## Naming Conventions
### Attributes
When you create entities or attributes that have more than one word in their name (for example, email address), use CamelCase. This means you use no white-spaces or underscores (“_”) and start each new word with an upper-case letter. Mendix will understand this, and everywhere the name of the entity or attribute needs to be shown, Mendix will output it as separate words and make those upper-case letters lower-case again. For example, “Email address” written in CamelCase is “EmailAddress.”
### Pages
Mendix naming conventions, a good name for this page would be Course NewEdit. This is because the page is going to be used for filling out the details of new course objects AND changing the details of existing courses.

## Work with Feedback
Work with Feedback
Once you have solved the errors and published your app, it is a good time to let your team preview the app to add their feedback and ideas.

When collaborating with your team, it’s a good practice to document planned work, add comments and feedback to current tasks, or else – so everyone knows what’s going on. This can be done via feedback.

If you decide to go this way, this can be done by using the feedback function. The floating feedback bar will give you a possibility to comment on the app.

All comments then will be visible on Mendix Developer Portal, on the Feedback page.

Feedback in the Publish App

![Feedback](/images/feedback.png "Feedback")

Feedback in Developer Portal

![Feedback in Developer Portal](/images/feedback_dev_portal.png "Feedback in Developer Portal")



# Mendix Studio Workshop Playlist
[Mendix Studio Video Playlist](https://video.mendix.com/categories/mendix-studio-workshop?page=2&slug=mendix-studio-workshop)
## Manual Domain Modeling
- Create App > Blank App > Edit App
- Domain Model editor (Left Menu)
- Create an `Entity`
  - `Entity` is like a database table
  - `Attribute` is like a field in the database
    - create a primary key
      - `_id` : `Autonumber`
```
Course

_id             Autonumber
Title           String
Description     String
Duration        Integer
Price           Decimal
```

```
TrainingEvent

_id             Autonumber
StartDate       Date and Time
EndDate         Date and Time
```

- In `TraningEvent`, Click the `->` to create an association
- Choose `Course`
- Make sure it's `[1 - *]`

## Spreadsheet to App
- Create App > Start with Data > Choose Spreadsheet > Import Data
- Preview > Manage Data

## User Interface
### Part 1
- Clicking an element in the Editor will bring up customization options at the right pane.
- Breadcrumbs > Row > Columns
  - Desktop: 4 columns
  - Tablet: window
  - iPhone: window
- If there a Cog Icon in the Editor, click `Container` in the Breadcrumbs and hit delete.
- Toolbox > Search Bar > type `Card`
- Add `Card Action` to each column
- 1st Card Action
  - Click the Icon to show the properties
  - Look for `Book` and change it
  - Rename the Caption to `Courses`
- 2nd Card Action
  - Click the Icon to show the properties
  - Look for `Map` and change it
  - Rename the Caption to `Locations`
- 3rd Card Action
  - Click the Icon to show the properties
  - Look for `User` and change it
  - Rename the Caption to `Trainees`
- 4th Card Action
  - Click the Icon to show the properties
  - Look for `Education` and change it
  - Rename the Caption to `Teachers`
### Part 2: Creating Overview Pages
- Click on `Book` Icon > Properties > Page
  - Note: `Page` will open a page when click
- Make sure `Create Object` is off
- Click Create new page
  - Title: `Course_Overview`
  - List > List Default
- Rename title in page as: `Courses`
- Remove subheading
- Click `List View` in Breadcrumbs
  - Requires an Entity (database)
  - In Properties > Database > Entity
    - Click dots, select `Course` Entity
- Map the values from the Entity to the List text
  - Click the `Title` inside the List
    - In Properties > Content
      - Click `Add attribute`
      - Select `title` attribute
    - Notice the `{}` curly brackets, it indicates value is drawn from an attribute
  - Do the next subheading and use `Description`
  - Do the next subheading and use `Duration`
    - Add a content `Duration: {} days`
- Add link to another Page
  - Click Details button
  - In Properties > Events > Page > Page (...)
    - Select `Course_NewEdit`
- At the Title Page section, click `Add` button
  - In Properties > Page
    - Entity (...), choose `Course`
    - Page (...), choose `Course_NewEdit`
      - Click the `Go to` (arrow) button
        - In Properties > General > Layout
          - Choose `PopupLayout`

### Part 3: Make Remaining Overview Pages
- Create a Page for Locations
- Click the Map Icon in the Editor
- In Properties > Page > (...)
  - Title: `Location`
  - Lists > List Default
- Change the Page Title to `Locations`
- Select `List View` and add an Entity `Location`
- Change the Title of a list to `name` from `add attribute`
- Do the same for the subheading, add `address` from `add attribute`
- Delete the 3rd subheading
- For `Details` button, Add a Page Link `Location_NewEdit`
- For `Add` button
  - Add Entity `Location`
  - Add Page `Location_NewEdit`
  - Click the `Go to` (arrow) button
    - In Properties > General > Layout
      - Choose `PopupLayout`
- Go to `Home` Page
- Repeat the steps for `Trainees` and `Teachers`
- For `Trainees`
  - `name`
  - `email`
  - `Trainee_NewEdit`
- For `Trainees`
  - `name`
  - `email`
  - `Teacher_NewEdit`

### Part 4: Create a page with a Data Grid
- Create a new `Card Action`
- Name it as `Events`
- In Properties > Page > (...)
  - Title: `TrainingEvent_Overview`
  - Grids > Datagrid Default
- Alternate Route: Creating Datagrid from scratch
  - Toolbox > Widgets > Data Grid
  - Drag to the Page Editor
  - Select an Entity `TrainingEvent_Overview`
- In Properties > Data Source > Attribute > (...)
  - In the `title` column
    - Choose `TrainingEvent_Course\Course/title`
- Delete the `end` column
- Add a new column, name it as `Location`
  - Select Attribute `TrainingEvent_Location/Location/name`
- Add a new column, name it as `Teacher`
  - Select Attribute `TrainingEvent_Teacher/Teacher/name`
- Add a new column, name it as `Start Date`
  - Select Attribute `start`
- Edit `New` button
  - Toggle `Create Object` to `ON`
  - Entity as `TrainingEvent`
  - Page as `TrainingEvent_NewEdit`
  - Layout as `PopupLayout`
- Edit `Edit` button
  - Page as `TrainingEvent_NewEdit`
- In DataGrid of the Editor
  - Go to Properties > Data Source > Search > Pencil Icon
    - Change attribute to `TrainingEvent_Course/Course/title`
    - Label: `Course Title`
 - In DataGrid of the Editor
  - Go to Properties > Data Source > Search > Add a Search Field
    - Change attribute to `Location....`
  - Go to Properties > Data Source > Search > Add a Search Field
    - Change attribute to `Teacher....`

## Migrating app projects to Mendix Studio Pro - Mendix Studio Workshop
- Migrating
  - Install Mendix Studio Pro (Desktop)
  - Open Mendix Studio Pro
  - Click `Open App`
  - Choose `Team Server`
  - In Team Server App dropdown list, Choose a project/app
  - Choose `Project directory`
  - Click `OK`
- Exploring
  - Toggle `Structure mode` and `Design mode` on the top right
  - Click `Domain model` on the left side pane (Project Explorer)
  - Click `Toolbox` at the very right tab and access `Widgets`

## Advanced Page Design
### Part 1 Nesting Data Views
- Project Explorer to add a button in the data grid
  - In the Page Editor,
    - Right click to where the other buttons are
    - Choose `Add button` > `Create`
    - Event `On Click` > `Blank` > `Blank` > `PopUpLayout`
    - `Toolbox` > `Widgets` > `Data widgets` > `Data view`
      - Note: Data views connect to a single object (record) in the database
    - Choose an Entity, OK
  - In `Toolbox` > `Building blocks` > `Headers` > `Pageheader Controls`
    - Select an Entity, and an Attribute
  - In `Toolbox` > `Widgets` > `Data widgets` > `List view`
    - Select `Data source` > Type: `Association` > Entity
  - Create a new `List view` inside of the previously created `List view`
    - Mind the association and use substitution

### Part 2
- Click the `Add` button to access Properties
- Use the associated entity reference to connect the other entity to the entity selected
Creating Forms for Registration
- `Toolbox` > `Forms` > `Form Vertical`
- Link the Form to an Entity
- Learn about `Substitution`

## Uploading Images/Photos
### Part 1: Plumbing
Update the domain model first, before adding image
- Go to Project Explorer > System > Domain Model
- Create an `Image` Entity that inherits from `FileDocument` Entity
  - This is called generalization
- Add a new Model in the Domain Model
  - name it as `TraineePhoto` and make a 1 to 1 association to `Trainee` Model
Adding a Microflow
- In Project Explorer > `YourAppName`
  - Right-click and select Add Folder name it as `Microflows`
  - Right-click `Microflows` and select `Add microflow...` name it as `CreateTrainee`
Microflows
- are functions
- Green circle: start
- Red circle: end
- Activity: actions
Create a new Activity
- Double-click on the action
- Select `Create object`
- Select `TraineePhoto` as Entity
Create a new Activity again
- Double-click on the action
- Select `Create object`
- Select `MyFirstModule.Trainee` as Entity
- Refresh in client: `Yes`
- Click `New` (to set `TraineePhoto` object as Member)
- Set Value as `$NewTraineePhoto`
Create a new Page
- Click the blue dot in the Microflows
- Select `Show Page`
- Object to pass: `NewTrainee`
- Page: click `Select...`
  - Click `YourAppName`
  - Click `Overview Pages`
  - Click `Trainee_NewEdit`
  - Click `Select`
Update `Trainee_Overview` page
- In Project Explorer
  - `YourAppName` > `Overview Pages` > `Trainee Overview`
  - `Events` > `On click`
  - Select `Call a microflow`, click `OK`

### Part 2: Implementing the Image Upload Widget
Integrate image uploading
- Go to `Trainee` page
Add Container
- Toolbox > Widgets > Container widgets > Container
  - Drag the `container` to the Page Editor
Add Data View
- Toolbox > Widgets > Data widgets > Data view
  - Drag the `Data view` inside the `container` to the Page Editor
  - `data view` will reference the `TraineePhoto` entity
Add Association to Data View
- Edit the `Data view`
  - Form orientation: Vertical
  - Data source > Entity (path): `TraineePhoto_Trainee` > `TraineePhoto` association
  - Do NOT automatically fill-in the contents of the view
Add Flex Container
- Toolbox > Building blocks > Alignments > Flex Container Right Center
  - Note: Building blocks are colelctions of widgets with styling added
  - Drag the `Flex Container Right Center` inside the `container` to the Page Editor
Add Image Viewer
- Toolbox > Widgets > File widgets > Image viewer
  - Drag the `Image viewer` nest inside the `Flex Container Right Center` to the Page Editor
Add Association to Image Viewer
- Edit the `Image viewer`
  - Select a Default Image
  - Data source > Entity (path): `YourAppName` > `TraineePhoto` association
  - Width: `100`
  - Height: `100`
  - Do NOT automatically fill-in the contents of the view
Add Flex Container
- Toolbox > Building blocks > Alignments > Flex Container Left Center
  - Drag the `Flex Container Left Center` inside the `container` (below the `Flex Container Right Center`) to the Page Editor
Add Image Uploader
- Toolbox > Widgets > File widgets > Image uploader
  - Drag the `Image uploader` nest inside the `Flex Container Left Center` to the Page Editor
Add Upload trainee photo button
- Toolbox > Widgets > Button widgets > Call microflow button
  - Drag the `Call microflow button` inside the `container` (below the `Flex Container Left Center`) to the Page Editor
  - Select Microflow: `YourAppName` > `Microflows`
    - Click `New`
      - Name: `UploadTraineePhoto`
Edit Upload trainee photo button
- Button style (uses Bootstrap): `Success`
- Click `Show microflow` to edit microflow
Editing Microflow
- Note: Microflows are functions run on the server
- Add an Activity and set it to commit to the `TraineePhoto`
  - Object > `Commit object(s)`
  - Object: `TraineePhoto`
  - Refresh in client: `Yes`
- Add another Action/Activity
  - Object > `Change object`
  - Object: `Trainee`
  - Commit: `Yes`
  - Refresh in client: `Yes`
  - Click `New` button
    - Member: `TraineePhoto`
    - Value: `$TraineePhoto`
- Press Ctrl + Tab to go back to Page Editor
Test setup
- In the Menu bar, click `Run` > `Run Locally`
- Click `Sychronize database` when prompted
Test run
- Go to App
- Click `Trainees`
- Click `Details` of a Trainee
- Try Uploading an image
Bonus: Overview page did not update uploaded image
- Go to Page Editor of Overview page
- Add a `Data view`
- Set entity associated to `TraineePhoto`
- and so on... just use the same steps as before
