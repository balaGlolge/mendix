# Mendix Studio Pro
![Layout Mendix Studio Pro](/images/pro_layout.png "Layout Mendix Studio Pro")

1. First of all, at the top of Mendix Studio Pro is the control bar. These are the menus and buttons, from left to right:

File– open and close documents and projects

Edit–all the options related to editing files, finding things in your project, and setting your preferences

View– from here, you can open all available tool windows

Project–all the functions related to working with Team Server (more about this later on)

Run–run and preview your app

Language– manage the language settings and access to language operations

Help– quick access to help environments

Run– deploy your app in the cloud or locally

View– preview your app

A button for opening your app in Mendix Studio

A button for opening the app Project Dashboardin the Developer Portal

A button that will take you to the Mendix App Store

The last dropdown menu provides access to all your apps, the Developer Portal, your profile, and the sign out button

2. At the top-left of Mendix Studio Pro, you see the Project Explorer (underneath the control bar). From here, you can access all the resources of the app (pages, microflows, and navigation, for example). The center of Mendix Studio Pro is the editor. This is where you will build all your resources.

3. On the right is the Toolbox, Properties, and Connector panes. You already know the first two. You can use the Connector to quickly connect an attribute to a widget or an entity to a list view.

4. At the bottom, you will find the Stories, Changes, and Errors tab. Here you can see the stories in your current sprint (and change their status). You can also see all the resources you have added or changed to the project and whether you have errors (and where they are).

# The Team Server
It allows you to collaborate with your team and use versioning. What's that? Have you ever heard of Subversion or GitHub? How about Dropbox or Google Docs? That's exactly what the Mendix Team Server is as well, only then for apps instead of files.

## Repositories
For every Team Server app, there is an online repository that contains both the model and all the app’s resources. You could compare the Team Server to a file cabinet of an architecture company, that has a folder for every building project (which is the repository for every app). Inside those folders are the building plans for each project, which the supervisors can use as a resource, so they know what the building should become (which are the app model and resources).

## Team Server Access
There are two prerequisites for accessing a Team Server project:
- You have to be a team member of the app project
- You need a role with permissions to edit the model (by default, this is the SCRUM Master or the Business Engineer role)

## Working Copy
A working copy is a local copy of the project. This local copy is what you work on and where you make all your changes. When you start working on your local copy, it starts to deviate from the original, which is stored in the repository on the Team Server. Working on your local copy has no effect on the repository. Once you are done with the changes, you can commit them, resulting in a new revision in the repository.

![Working Copy](/images/working_copy.png "Working Copy")

## Status and Changes
Different kinds of changes are visualized with the following icons:
![Status Changes](/images/status_changes.png "Status Changes")

## Committing Changes
Sending changes to the repository is called committing. The idea is that you commit small, consistent pieces of work to the repository (for example, implementing a new feature and fixing a bug).

Mendix Studio Pro also attaches some information automatically:
- The author (the user who committed)
- The date and time of the commit
- The list of changed content (documents/folder/modules), along with the type of the change (modify, add, delete, etc.)
- The version of Mendix Studio Pro that was used to commit

## Update
Committing is only possible when your working copy is up to date with the repository. If someone else committed a change since the last time you updated, you have to update first.

## Get the Latest Version of the LearnNow App
Option 1: I am now starting with the learning path
If you’re starting from scratch, follow the instructions below to prepare the training project and content.

Import the Project Package
We’ve provided a project package that you can use to create a new project. It contains all the required development content up to this point.

Download the Project package from the Resourcestab.

In Mendix Studio Pro, select File > Import Project Package.

Select the downloaded package.

Select a Location on your drive to store the project files.

On the Import Project Package dialog box, select Team Server and upload to a New repository.

Enter LearnNow Management for the App name, and click OK.

Import the User Stories
Download the User stories from the Resources tab in the training environment.

In Mendix Studio Pro, click Project Dashboard to go to your project’s dashboard in the Developer Portal.

Select Collaborate > Stories in the sidebar menu.

Click More.

Select Import/Export.

Select Update stories from Excel and then click Browse.

Select the User stories Excel file and click Import.

Click Next to import the sprint and user stories:

Click Develop > Planning in the sidebar menu.

Mark the Get started sprint as completed.



Option 2: I already have a project and I want to Update My Module
If you want to make sure your model is up to date for the assignments in this module, you can update your model with a specific module we’ve provided. Follow the instructions below to update your existing model.

Import the Module Package
Download the Module package from the Resources tab in the training environment.

Open your LearnNow Management project in Mendix Studio Pro.

Go to the Project Explorer, right-click on the project name and select Import module package.

Select the downloaded module.

Select Replace existing module for the Action, and then select LearnNow Management for the Module to replace (or MyFirstModule if you haven’t renamed it).

Click Import.

Set Up Your Navigation
Open the project Navigation.

Add the following navigation items:

![Navigation Items](/images/navigation_items.png "Navigation Items")

It should look like this in Mendix Studio Pro:
![Navigation Items in Studio Pro](/images/navigation_items_in_studio_pro.png "Navigation Items in Studio Pro")

That’s it! You’re all set to do the assignments. Go ahead and continue with the next module.

# Automating Processes
In this module you will learn how to use Mendix Studio Pro to make your app more efficient by adding custom logic using microflows. In detail, you will learn how to:
- Set up a widget event to trigger a microflow
- Create a microflow to change objects and values
- Solve errors to ensure your microflows work as intended
- Give indications to the users on what information they still need to fill out

## Automatically Fill End Date
In the image below, you can see that, when Jimmy selects a Course and Start Date for a Training Event he is about to create, the End Date is automatically calculated. Note that European date format is used in the images of this course.

![Auto Fill End Date](/images/auto_fill_end_date.png "Auto Fill End Date")

Let's formulate a plan for building this functionality. You will need a couple of steps:

1. The first step is to make sure the microflow is triggered. As the start date or the course type determines the end date, a trigger should be set there. You can create this trigger by using a widget event. You will need to add a widget event to the start date input widget and the course selector. The widget event will trigger a microflow that calculates the end date. Obviously, you will need to create the microflow itself as well.

2. The second step is to fill out the calculated end date. For this you will need to change the TrainingEvent (Change Object activity) and set the new EndDate value. You are going to use a microflow expression for this, the addDays function to be specific. This function adds a number of days (the duration of the course) to a date (the start date).

3. After that, you deploy the app and test the functionality by entering data in the detail page in every way possible and see if you can cause errors.

4. Next step is to learn how to analyze any errors that may have occurred, and adjust the microflow to prevent these errors from happening again.

5. Finally, you will commit your work.

## Triggering a Microflow from an Input Widget
The difference with input widgets is that the events can be triggered at three different points:
- On enter: when the user enters (clicks on) the input widget
- On change: when the user leaves the input widget after making a change
- On leave: when the user leaves (closes) the input widget (no matter whether they changed the value of the widget or not)

For example, the input widget that changes the StartDate value can trigger a microflow:
- On enter: Then the microflow will be triggered once the user clicks on the agenda icon
- On change: Then the microflow will be triggered once the user changes the start date of the training event. That could also mean that they change the value of the StartDate from “no selection” to a specific date.
- On leave: Then the microflow will be triggered once the user opens the date picker and then closes it again, no matter whether the changed the date or not.

### Set up the Input Widgets
#### Start Date Input Widget (Date Picker)
1. In Mendix Studio Pro, open the TrainingEvent_NewEdit. You can double-click on elements in Mendix Studio Pro to adjust their properties, just like using the Properties pane in Mendix Studio.

2. Double-click on the start date input widget to open its properties. A pop-up window opens. This window allows you to control the settings of the input widget. There are four tabs in this window: General, Common, Events, and Appearance. Open the Events tab. In this case you want to calculate the end date when the start date has changed, so you need an On change event.

3. Set the On change event to Call a microflow. A selection window opens which allows you to select one of the existing microflows or create a new one. The microflow to calculate the end date doesn't exist yet. Click New to create a new microflow.

4. Remember the naming convention for microflows? Prefix_Entity_Operation. The prefix for an On Change event is OCH. Give the microflow a clear name, according to the naming convention. This way it will be easier for another developer to interpret what it is and what it does, should the need arise. A good name is: OCH_TrainingEvent_CalculateEndDate.

![End Date Picker](/images/end_date_picker.png "End Date Picker")

#### Course Input Widget (Drop Down)
As each course has a different duration, the end date also changes when a (different) course is selected. This means the course selector also needs to trigger the same microflow.

1. Go back to the view of TrainingEvent_NewEdit add an On Change event to the course selector and connect the OCH_TrainingEvent_CalculateEndDate microflow to it.

![Course Input Widget](/images/course_input_widget.png "Course Input Widget")

2. Open the newly created microflow. See how it has a TrainingEvent parameter? This represents the TrainingEvent the end user is currently creating or editing.

### Build the Microflow

The goal of this microflow is to use the start date of the training event and the duration of the course to calculate the end date of the training event. For this you will need to change the TrainingEvent (Change object activity) and set the new EndDate value. You are going to use a microflow expression to calculate the new end date: the addDays function to be specific. Microflow expressions are where you get to write a little bit of code, to add even more custom logic to your app. The addDays function adds a number of days (the duration of the course) to a date (the start date).

Common Gotcha: You need to click `Show` on the Microflow inside Edit Reference Selector (when you double-clicked a widget) to show the Microflow Editor.

1. The first thing you need to do is add an Action activity to the microflow and then convert it to a Change object. Do this by clicking the activity icon in the microflow toolbar and then clicking on the flow.

2. Place the Action activity close to the end event. Remember you always start with the end result! Now to convert to a Change object, you right click the Action activity and set the action type to Change object. After doing this, double click the activity again to open its Properties. The object you are about to change is the TrainingEvent object, so select that as the input variable.

3. Underneath Refresh in client, click New to add a change. The Edit Change Item pop-up will open. First you have to select which Member you will change. A member is either an attribute or an association. In this case you want to change the EndDate attribute, so select that in the dropdown. Immediately, the expression editor (the big text area) becomes editable.

The **expression editor** is where you are going to write an expression to add custom logic to your app.

![Expression Editor](/images/expression_editor.png "Expression Editor")

## Microflow Expressions

Your biggest friend when writing microflow expressions is the keyboard shortcut **ctrl + space**. When you use this shortcut, you will get a list of all the elements you have available to you to create your microflow expression.

The following types of element are available:

Functions: there are many functions available to change or compare values or to extract information from values. An exhaustive list can be found in the [Microflow Expressions](https://docs.mendix.com/refguide/expressions). You can also access that list by pressing F1 while on the expression editor. Functions always need **parentheses ()** behind them to work. Inside the parentheses you place the ingredients the function needs to work its magic! So it's **functionName(Ingredient 1,Ingredient 2)**.

Variables contain a single object, a list of objects, or a primitive (single) value. A variable always starts with a `$`(dollar sign) and the name of the variable. Every piece of data in a microflow is stored in a variable and has a unique name.

For example, the Trainee object is stored in the `$Trainee` variable. Attributes of an object are added behind the variable: `$Trainee/EmailAddress`.

Tokens are DateTime related, except the Current User token. Get a list of suggestions by typing `[`.

For example, to use the current date and time, use `[%CurrentDateTime%]`

These are some general expressions:

![General Expressions](/images/general_expressions.png "General Expressions")

### Examples of microflow expressions
You can use the **round** function to round a number. If the value of the variable `$Number` is 0.99, then the outcome of the function **round(`$Number`)** will be 1.

You can use the **toLowerCase** function to transform text to lowercase. For example, if the variable `$Name` has ‘BeStName3veR’ as a value, then the **toLowerCase(`$Trainee/Name`)** function will set the value Name to ‘bestname3ver’.
