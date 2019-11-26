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

### Create an Expression to Calculate the End Date
From the previous assignment, the Expression Editor is open. That will allow you to enter the function which will calculate the End Date of the Training Event. You will need the addDays function. In this case, the addDays function will add the duration of a course to the start date.

1. Click inside the microflow expression editor and press ctrl + space. Start typing addDays and, once you see it in the list of options, select it by pressing Enter or double-clicking it.

2. Now add the parentheses after the addDays function. The function becomes red. This is because Mendix Studio Pro now recognizes it as a function and is telling you there are ingredients missing. Mendix Studio Pro even tells you which ingredients are missing and in what order they should be placed between the parentheses. In this case the first ingredient is a Date and time value and the second ingredient an Integer or Long. So the function will be addDays(Date and time, Integer/Long).

3. So the function will be addDays(Date and time, Integer/Long or, if you relate that to your Domain Model and the calculation you are creating: addDays([start date], [duration]).

4. Go ahead and see if you can place both attributes between the parentheses. A couple of important things to remember:

- Always use ctrl + space, don't just start typing blindly.
- Attributes of an object are always written after the variable representing that object (so start from the variable, not directly with the attribute). Notation: $[VariableName]/[AttributeName].
- Separate the ingredients by placing a comma in between them.

5. Could you add the Duration ingredient? Most probably not! This isn't your fault though! You can access the StartDate from within the TrainingEvent variable that is available in the microflow ($TrainingEvent/StartDate). You can even see which Course was selected ($TrainingEvent/MyFirstModule.TrainingEvent_Course). You can't however then go into Course by typing / again to get to the Duration. Learn more about how you can tackle that in the next lecture!

## Microflow's Scope
When you have an object available to you in a microflow (this is also called in the microflow’s scope), you have access to all the information inside the object (the attributes) and the objects it is connected to (the associations), as you can see in the image below. You don't have access to the information inside those objects though.

![Microflow Scope](/mendix-pro/images/microflow_scope.png "Microflow Scope")

So, the TrainingEvent object is in the microflow’s scope and the StartDate is inside that object so it's also in scope. Because the Duration is in the Course object, it is not in scope yet. You will need to get it into your microflow: you need to do a **retrieve**. You will learn what a retrieve is and how to do a retrieve in the following lectures.

## Retrieving Data
Retrieving Data
As we have seen, sometimes data you need for your microflow isn’t in scope when you start building the microflow and the way to bring it into scope is a retrieve. A retrieve is an activity in a microflow, just like the Change object and Create object activities. Specifically, what a retrieve does is to look for a specific object in a list of objects and to make it available in the microflow.

When you do a retrieve, you have to decide where you want to get your information from: memory or the database. First let's take a look at where your data is at what point.

![Retrieve Data 1](/mendix-pro/images/retrieve_data_1.png "Retrieve Data 1")

Let’s start with an example. When you start writing a text document, you boot up your computer, start your text editor, and open a new text document. At that moment you see your text document on your screen (**1**), and the document is loaded in memory (**2**). When you make changes, they are visible on the screen (**1**), and are recorded in the device’s memory (**2**). If you close the document without saving it, the document that’s in memory will be deleted (**4**) and the document won’t exist in the memory or on the hard drive anymore.

However, if you save the document, it is stored on the hard drive (**3**) and, when you close the document, the document that was in memory will be deleted (**4**) but will remain on the hard drive (**3**). When you reopen the document (**3**), it will be loaded into memory (**2**) and will be visible on the screen. When you make changes to the document, they’ll be stored in memory (**2**). When you save the document, the saved file on the hard drive (**3**) will be updated with the changes that are in memory (**2**). But, if you cancel the changes, the changes in memory will be deleted (**4**), and the document copy on the hard drive will remain as the original saved document.

So, you might be wondering, what does this have to do with a Mendix application?

![Retrieve Data 2](/mendix-pro/images/retrieve_data_2.png "Retrieve Data 2")

Let’s look at another example. When you add a new location to the application, the user clicks the new button, which results in the creation of a new empty Location object in memory (**2**). The object is then sent to the client (**1**), where you can edit it. When you make changes, they are visible in the client (**1**) and will be recorded in memory (**2**). If you don’t save it, and cancel the Location object, you will close the page. The Location object as stored in memory will be sent to the garbage bin (**4**). The Location object won’t exist anymore in memory (and there was never a Location record in the database).

However, if you save the Location object, it will be stored in the database (**3**) as a new record, and the Location object as memorized in memory will be sent to the garbage bin (**4**). Once you reopen the Location details, the Location record as stored in the database (**3**) will be loaded into memory (**2**) as the Location object, and will be visible in the client. Once you make changes to the Location object, these changes will be recorded in memory (**2**). Once you save the changed Location object, the database record (**3**) will be updated according to the changes in memory (**2**). Or, if you cancel the changes, the Location object as recorded in memory will be sent to the garbage bin (**4**), and the Location record in the Database will remain as the original saved object.

It is important to see the similarity of the interactions here in the following ways:
- client <–> memory <-> database
- editor <-> memory <-> hard drive

## By Association Retrieve
Doing a retrieve from memory in Mendix is called a “By Association Retrieve”. This means the app will look in memory for the requested information first. If it isn't in memory yet or if the information could be outdated (because the information is older than a certain threshold), the app will get its information from the database.

When the information is already in memory, the By Association Retrieve is faster than a Database Retrieve. This is because no connection to the database is needed. This is one of the benefits of using a By Association Retrieve.

Another reason to use the By Association retrieve is when you want to retrieve information that isn't in the database yet. Remember the jam example? Let's say you are making a new type of jam. The director wants to sample the new flavor. This jam isn't available in the warehouse (the database) yet, so you'll have to get the sample straight from the production line (memory).

An object that has been created in memory is called a transient object. Doing a By Association retrieve will include all information in the database, plus the transient objects that are available in memory. This can be useful, like in the example above with the new jam flavor, but it can also be a risk.

Let's go back to the jam factory. The director wants an overview of all jam types that are currently being sold. The new jam flavor, that is being produced and tested now, but hasn't been approved for sale yet, shouldn't be in this list. This means you will have to ask the warehouse employee for the list (the database) and not the production line employee (memory).

So, transient objects are always included in a By Association Retrieve. If you don’t want transient objects to be included, use a From Database Retrieve.

### Retrieve Your Data
Time to get that Course object into the scope of your microflow! As microflows work sequentially, from left to right, the Course object needs to be retrieved before the **Change object** activity. Otherwise it won’t be in scope for the microflow expression in the **Change object** activity.

1. Place a new activity on the microflow line (to the left of the **Change object** activity) and double-click the new activity to set the type of action. Select **Retrieve**.

![Microflow Retrieve](/mendix-pro/images/microflow_retrieve.png "Microflow Retrieve")

You now need to decide what your data source is going to be: **By association** or **From database**. In this case it needs to be **By association**. There are two reasons for this:

- You may create a new TrainingEvent, where the information isn't in the database yet. The Course object is, but the connection to the Course isn't and that is the starting point of the retrieve.

- You may be editing an existing TrainingEvent and have changed the Course type. If you would look up the connection in the database, you would get the old Course type, not the one you just selected.

2. Click **Select** to select the association you want to use for this retrieve, in other words: which object you want to retrieve. Select the TrainingEvent_Course association. Click **Select** and in the next screen click **Ok**.

![Select Association](/mendix-pro/images/select_association.png "Select Association")

![Retrieve Objects](/mendix-pro/images/retrieve_objects.png "Retrieve Objects")

3. Open the **Change object** activity and go back to the addDays function. You now have the NewCourse object in scope as the $NewCourse variable, so you have access to the Duration attribute. Complete the microflow expression as shown below:

### Common Gotcha - Unknown variable NewCourse
Use **Course** instead of **NewCourse**

![Edit Change Item](/mendix-pro/images/edit_change_item.png "Edit Change Item")

## Run, Test, Crash
Time to test your app! There are two ways to run your app from within Mendix Studio Pro: Run and Run Locally. Run deploys the app to the cloud environment, just like Publish in Mendix Studio Pro. Run Locally creates a local running version of your app, which exists only on your computer.

Remember the goal is to try and break the application, so be creative and try scheduling a training event in every possible way.

1. Click Run Locally to quickly deploy the app. This is faster than using Run to deploy it in the cloud, so when developing you always want to use Run Locally.
The first time you use Run Locally, you will see the following screen:

![Crash 1](/mendix-pro/images/crash_1.png "Crash 1")

2. The local running version of your app uses its own database. The first time you use Run Locally, this database doesn't exist yet, so you have to create it. Click Yes and wait for the app to deploy. Once you see the confirmation that the deployment is complete, click View to preview your app.

![Crash 2](/mendix-pro/images/crash_2.png "Crash 2")

3. Go ahead and create a couple of courses, locations, teachers and trainees. Once you have done that, continue the exercise and see if you can "break" your app!

![Crash 3](/mendix-pro/images/crash_3.png "Crash 3")

4. Yeah you did it! Usually an app crashing isn't something to celebrate. In this case however it was the goal of the assignment and now you will learn how to debug your app to figure out what is wrong. The minute you select the course or StartData your app will crash!

### Common Gotcha
If you broke your App and can't seem to fix it. Feel free to go Import a new LearningNowApp and work on it instead. Refer back to Learning Path > Rapid Developer (Analyst) > Mendix Studio Pro

## Analyze Errors
The next step is to analyze the errors.

1. In Mendix Studio Pro open the **Console**. This is the local log of your app and this is where error messages will appear if your app crashes.

![Error 1](/mendix-pro/images/error_1.png "Error 1")

2. The two red lines at the bottom represent the error that you just triggered. Double-click on the line that has the paperclip icon to investigate it further. When errors like this occur, Mendix tries to give you a very clear log message, to give you a good starting point of how and where to fix the error.

3. In the message you can see the name of the microflow that the error occurred in (highlighted in red in the following image). It's the OCH_TrainingEvent_CalculateEndDate microflow that you are currently building! Let's do some debugging do see what is causing the error.

### Tip: If you want to know more about creating log messages within Mendix, take a look at the Advanced module Learn How To Handle Errors.

4. Open the **OCH_TrainingEvent_CalculateEndDate** microflow and right click on the first activity. Click Add breakpoint. A red dot should appear at the bottom right corner of the activity. This breakpoint will pause the microflow when it passes this activity, allowing you to investigate the microflow step by step.

![Error 2](/mendix-pro/images/error_2.png "Error 2")

5. Go back to your app, refresh the browser and repeat the steps you took to make the app crash (select the Course or Start Date). The Mendix icon in your taskbar will start flashing when the microflow is paused.

6. Go back to Mendix Studio Pro. Make sure you have the Debugger and Variables windows visible (if you don’t, go to View, then Debug windows). Setting up your Mendix Studio Pro like the following image, with the Debugger and Variables windows displayed side by side, is recommended.

![Error 3](/mendix-pro/images/error_3.png "Error 3")

7. The activity with the red border around it, is the activity that the microflow is currently paused on. It pauses before the execution of the activity, so the retrieve hasn't been done yet at this point. Click **Step over** in the Debugger window to go to the next activity. Investigate the Variables window to see if you can figure out what's going wrong.

![Error 4](/mendix-pro/images/error_4.png "Error 4")

8. The Course was retrieved successfully, but the StartDate is **empty**. This will cause the addDays function to crash, because one of the two ingredients is still missing. This makes sense though, because when filling out the details of the new training event you can't select both the Course type and the start date at the same time. If you had chosen a start date first, you would get the exact same crash, only then the Course object would be missing instead of the start date. How can you prevent this from happening? By building in checks to see whether all necessary ingredients are there, before executing the addDays function.

9. Click **Continue** in the Debugger window to finish the debugging process.

## Use Decisions
You build checks into a microflow with decisions, the yellow diamond-shaped component. In this case you can use it to check whether both a start date and a course have been selected, before allowing the microflow to continue.

You will need two decisions in this microflow, one to check the start date and one to check the course.


1. Place a decision on the microflow line, in between the two existing activities. Double-click it to open its properties. The first thing you should decide on is the Caption. This will be displayed on the decision. A good caption will allow you to understand what the decision checks, without having to open it. This decision will check whether the start date has been selected, so a good caption would be: **Start date selected?**

2. The next thing you need is the microflow expression. This is where you define what needs to be checked. Checking whether the selection has been made will result in a **true** or **false** outcome. The **true** value should always represent the positive outcome, in other words when the check results in a **true**, the microflow continues. When the result is **false**, the execution is canceled. To make sure that the **true** value represents the 'everything is ok' outcome, you need to write the check (or question) in a way which may feel counterintuitive at first. Instead of asking whether start date is **empty** (this is the value if no selection has been made), you are going to ask whether it is NOT empty. Is not is written as !=. The expression in this case is **$TrainingEvent/StartDate != empty**.

3. Click **OK** to go back to the microflow.

4. The arrow coming out of the decision is now red. This is because the flow doesn't know which value from the decision it represents. It's basically having a bit of an identity crisis! Right click the arrow and then set the **condition value** to **true**. This flow now represents the everything is ok outcome and continues to calculate the end date. The decision also needs a flow for the false path. Click the bottom corner of the decision and draw a line downwards. On release select **End event**. This path automatically becomes the false path because this decision only has two possible outcomes. So if one path is true, the other one is automatically false.

![Use Decision 1](/mendix-pro/images/use_decision_1.png "Use Decision 1")

5. Repeat these steps to build the decision that checks whether the Course has been selected. Remember that the Course object is stored in the $NewCourse variable. You need to check whether that variable is empty or not.

6. Use the following image to check your solution

![Use Decision 2](/mendix-pro/images/use_decision_2.png "Use Decision 2")

7. Full microflow should now look like this:

![Use Decision 3](/mendix-pro/images/use_decision_3.png "Use Decision 3")

## Finish the Microflow
The final steps are to finish the microflow, to save your work, and commit it.

1. Right click the first activity and click **Remove breakpoint** to remove the breakpoint. This way the app will no longer pause and go into the debugger when the microflow is triggered.

2. Run the app again (**Run Locally**) and try scheduling a training event. There is one error left, but this is a different kind of error. The app won't crash any longer, so what could it be? Take a look at the date that is being calculated and see if you notice the problem. If you don't see it, create a course with a duration of one day and schedule that course. The end date is one day later than the start date, but a course that lasts one day starts and finishes on the same day! The addDays function basically adds 24 hours, so the function is correct but not completely what you need here. Let's change the logic a little bit!

3. Go back to the microflow and open the **Change object** activity. Edit the addDays function so it adds the duration of the course, minus one day. This way a course that lasts one day will now start and finish on the same day. Simple add “– 1” after $Course/Duration to achieve this.

![Finish Microflow](/mendix-pro/images/finish_microflow.png "Finish Microflow")

4. Do one last round of testing and then continue on to the last step!

## Commit Your Work
Congratulations! You have automatically calculated the end date and have now made the scheduling of training events more efficient in three different ways! Time to commit your work and update the status of the user story.

1. Open the **Changes** pane, you will find it at the bottom of Mendix Studio Pro.

![Commit Work 1](/mendix-pro/images/commit_work_1.png "Commit Work 1")

There are currently two changes.

2. Click **Commit** to start the commit process. Mendix Studio Pro first does an automated check for updates and after that the commit window will open.

3. In the **Commit** dialog box in Mendix Studio Pro, click the **Changes in model** tab. Here you can also see the changes you are about to commit to the Team Server.

![Commit Work 2](/mendix-pro/images/commit_work_2.png "Commit Work 2")

4. Next, open the **Related stories** tab again and select the task for automatically calculating the end date. You’ll find it in the fourth user story.

5. The text area above the tabs is where you have to enter a commit message. This is required to go through with the commit. It is of course always a good idea to make this commit message a descriptive one. How about: “Added two on change events to the TrainingEvent_NewEdit page, on the Course and StartDate input widgets. Added a microflow that calculates and shows the correct EndDate based on the Course and the Startdate”.

6. Click **OK**. The commit will take a couple of seconds. Once it's done, there will be 0 changes left in the Changes pane.

7. Now, go to the Developer Portal to check out your commit! On your app project page in the Developer Portal, click **Team Server** to see all the commits. Your commit is all the way at the top, because it is the last commit.

8. Click **Details** for your commit to go to the **View Revision** page where you can read more about the details of the revision.

9. Go back to Mendix Studio Pro and open the **Stories** pane. Set the current user story to **Done**.

## Automatically Calculating the Total Number of Registrations
Jimmy has one last request for custom logic, as described in the next user story: **As a teacher, I want to be able to see the number of trainees attending a training event at any time, so that I know what resources I need**.

Each training event can host a maximum of 12 trainees. However, it would be a waste of money if the teacher always ordered lunch or prepared handouts for 12 people, if there are only 6 trainees coming to a training event. It would therefore be very useful if the teachers could easily see how many people are registered for each training event.

To build this functionality, you need to take a couple of steps:

1. Make sure you can see the information in the app

2. Determine when the number of registrations should be calculated.

3. Build the microflow that calculates the total number of registrations.

4. Deploy and test your work.

5. Commit your changes to the team server.

Check the next lecture to learn more about the difference between stored and calculated attributes!

## Stored vs Calculated Attributes
You want to show a new piece of dynamic information in your app: the total number of registrations per training event. If you want to show dynamic information in your app, it needs to be represented in the Domain Model as an attribute. In this case the total number of registrations says something about the training event, so you add the new attribute to the TrainingEvent entity. A good name for this new attribute is TotalNumberOfRegistrations and the type is Integer. You can have one or seven or twelve registrations, but never one and a half registration or eight and three quarters registrations.

You also need to decide whether this attribute will be a stored or calculated attribute. The value of a stored attribute is saved in the database. The value of a calculated attribute is calculated when it needs to be shown in the app. The calculation is done by a microflow. Note that this microflow will be triggered every time the value is shown or used in the app.

The rule of thumb when it comes to deciding between a calculated or a stored attribute is the following: if a value changes more often than you look at it, make it a calculated attribute. If you look at it more often than it changes, store it in the database.

A good example for a calculated attribute is if you want to show the latest exchange rates in an app. These are values that change all the time. That is why it is a good idea to make this a calculated attribute. Now let’s see how that plays out for the TotalNumberOfRegistrations attribute.

As stated earlier a maximum of 12 people can attend a training event. For a fully booked training event that means the total number of registrations changes 12 times. Now let’s say some of the trainees cancel their registrations and other trainees register in their place. That would mean the total number of registrations changes 16 to 20 times at most. This won’t happen all that often and most likely the teachers using the app will look at the information more often than this takes place. So in this case, the total number of registrations should be a stored attribute.

## Add a New Attribute
1. Go ahead and add the attribute TotalNumberOfRegistrations to the TrainingEvent entity. As explained in the previous lecture, it should be a stored attribute of the type Integer. This attribute also needs to be shown to the teachers in the app. A good spot for that would be on the TrainingEvent_Overview page. This way, when the teacher looks at his schedule, he immediately sees how many people are registered for each training event.

2. Open the TrainingEvent_Overview page and add the attribute to the list view. From the Toolbox, add the **text** widget underneath __At {…/Name}__. Double-click it to open its properties. Click the topmost **Edit** button to edit the caption.

3. Add a new parameter (dynamic text) by clicking **New**. Select the TotalNumberOfRegistrations attribute.

4. The caption is the text that will be shown to the teacher. Replace __Text__ with __Number of registrations: {1}__. The __{1}__ will be replaced by the TotalNumberOfRegistrations parameter.

![Add New Attribute 1](/mendix-pro/images/add_new_attribute_1.png "Add New Attribute 1")

That's what it should look like at the end:

![Add New Attribute 2](/mendix-pro/images/add_new_attribute_2.png "Add New Attribute 2")

## Object Event Handlers
You have decided that you are going to store the total number of registrations in the database. Now you need to determine when this number changes, in other words when you are going to (re)calculate and store it in the database. When does the total number of registrations for a training event change? Exactly! When a new registration is added to the system or when an existing registration is deleted. And not just in some cases, no, every time a registration is added or deleted the total number of registrations needs to be recalculated.

You already know how to create buttons that trigger a microflow. You could add the logic for this user story to a custom save and a custom delete button. Every time a teacher adds or deletes a registration the total number would be recalculated. However, if an automated process were to delete a registration (for example when the trainee that the registration belongs to is deleted), the recalculation wouldn’t happen, because those specific buttons aren’t clicked. This means the custom buttons aren’t the answer to the problem. You need object event handlers!

Object event handlers “listen” to the app, waiting for events to occur. Events are when an object is created, committed, deleted or rolled back (canceling of changes). You can then select a microflow that can be triggered **before** or **after** the event is executed. In the case of your current user story you need an after commit and after delete object event handler. You add object event handlers to the Domain Model, on the entity that the event occurs on. In this case that is the Registration entity. Let’s add them now!

You need two object event handlers: one for **after commit** and one for **after delete** of a registration. Both object event handlers will use the same microflow (this microflow doesn’t exist yet). It is a best practice to reuse logic when possible, because this makes your app easier to maintain later on. By making both event handlers trigger the same microflow, you reuse logic!

Follow the instructions in the next lecture to see how you can add object event handlers in your app!

### Add Object Event Handlers
You need two object event handlers: one for **after commit** and one for **after delete** of a registration. Both object event handlers will use the same microflow (which you will also need to create).

1. Open the Domain Model and double-click on the Registration entity. The fourth tab is the **Event handlers** tab. Open this tab and click **New** to add a new event handler.

![Add Object Event Handlers 1](/mendix-pro/images/add_object_event_handlers_1.png "Add Object Event Handlers 1")

2. First you will set up the after commit object event handler. Set the **Moment** to **After** and the **Event** to **Commit**. Click **Select** to select the microflow that should be triggered.

3. Click **New** to create a new microflow. You now need to come up with a good name for this microflow. Remember the naming convention __Prefix_Entity_Operation__?

These are the prefixes for the object event handlers:

![Add Object Event Handlers 2](/mendix-pro/images/add_object_event_handlers_2.png "Add Object Event Handlers 2")

4. Because this microflow will be for both the After Commit and After Delete, you have to add both prefixes to the name of the microflow. Like this: ACO_ADE_Registration_SetTotalNumberOfRegistrations.

![Add Object Event Handlers 3](/mendix-pro/images/add_object_event_handlers_3.png "Add Object Event Handlers 3")

5. Click **OK** in this screen and in the next screen to finish the process.

6. Now repeat these steps to add the After Delete object event handler, but instead of creating a new microflow, select the ACO_ADE_Registration_SetTotalNumberOfRegistrations microflow you just created.

7. Close the properties window of the Registration entity and look at the entity in the Domain Model. See how there is a lightning bolt to the left of the entity name? This tells you that this entity has one or more object event handlers.

![Add Object Event Handlers 4](/mendix-pro/images/add_object_event_handlers_4.png "Add Object Event Handlers 4")

### Create a Registration List
Open the ACO_ADE_Registration_SetTotalNumberOfRegistrations microflow. It is an empty microflow with an input parameter of type Registration. This is the registration that was just committed or deleted. Let’s formulate a plan for building this microflow:

- The end result of this microflow is to store the total number of registrations in the TrainingEvent object owning the registration that was just committed or deleted. You also want to show the updated value in the client.

- This TrainingEvent object isn’t in scope of the microflow yet, so you need to retrieve it. This retrieve needs to be by association. It is by association and not from database because if the Registration object was just deleted from the database, the connection to a TrainingEvent also won’t exist in the database anymore. It does however still exist in the input parameter of this microflow.

2. To get the **TrainingEvent** in scope, add a new activity just after the start event of the microflow. Set the type to **Retrieve**, the source to **By association** and from the Registration entity select the **Registration_TrainingEvent** association.

3. To store the number of registrations for each training event, add a new activity just before the end event. Set the type to **Change Object** and from the variable list, select the **TrainingEvent**. Click **New** and select the **TotalNumberOfRegistrations** attribute. Set the value to **$Count** (this won’t work at this moment, but don’t worry – you’ll create this variable in a later step).  Also, change the **Commit** to **Yes**. Otherwise the registrations go away, and the count is zero when the app is closed and opened up again.

![Create Registration List 1](/mendix-pro/images/create_registration_list_1.png "Create Registration List 1")

Now you have the beginning and the end of the microflow. But the microflow doesn’t really do anything yet. What you need to do next, is to determine the total number of registrations and set this as the new value (change it) of the TrainingEvent object.

Since the microflow doesn’t know whether the After Commit or After Delete object event handler was triggered, you can’t use a +1 or – 1 solution. Instead, you need to **count** all Registrations that belong to this TrainingEvent. But you don’t have all Registrations in scope of the microflow yet, only the one that was just committed or deleted. This means you have to do another retrieve!

As a reminder: An object that has been created in memory but isn't in the database (yet) is called a transient object. Doing a by association retrieve will include all information in the database, plus the transient objects that are available in memory. In this case you don’t want transient objects to be counted, because you only want those registrations that have been stored in the database. If you have registrations that exist in work memory, but not in the database yet, you don’t want to count them in this microflow. You need to do a **from database** retrieve!

4. Add a new activity to the microflow, directly after the first retrieve activity. Set the type of action to retrieve and the source to From database. Click **Select** to select which entity should be retrieved.

5. In the following image you can see that there are two options to select the Registration entity. One at the bottom of the select window (underneath MyFirstModule) and one that is nested in the TrainingEvent variable at the top of the window. If you were to use the bottom option, you would get all Registrations in your microflow. That’s not what you want here, you only want those Registrations that belong to this TrainingEvent. That is why you should use the nested option at the top of the screen, so you use the TrainingEvent as a constraint.

![Create Registration List 2](/mendix-pro/images/create_registration_list_2.png "Create Registration List 2")

6. The Name will automatically be set to **NewRegistrationList**, because it is a list of registrations. The last step is to count the registrations and set the value of the TotalNumberOfRegistrations attribute to this in the Change object activity. Counting is done with an activity (what a surprise!), the **Aggregate list** activity. Add a new activity to the microflow, directly after the second retrieve. Set the type of action to **Aggregate list**. Use the following settings to configure the activity:

![Create Registration List 3](/mendix-pro/images/create_registration_list_3.png "Create Registration List 3")

7. Your microflow should now look like this:

![Create Registration List 4](/mendix-pro/images/create_registration_list_4.png "Create Registration List 4")

#### Run and Test the Functionality
8. Congratulations, you have built the functionality! Time to see it in action! Run your app and add a couple of registrations to a training event to see it work.

9. You might be asked to synchronize your database due to the changes we did to the Domain Model.

![Create Registration List 4](/mendix-pro/images/create_registration_list_4.png "Create Registration List 4")

#### Commit your Work
10. Once you have added a couple of registrations to your app, go ahead and commit your new functionality to the team server. Also set the user story to Done. You are doing great!

## Summary
In this module you have learned how to automate certain processes within your app. Specifically, you have learned:

- How to automatically fill out fields, such as the end date of a training event, when the course and start date are given

- How to trigger a microflow from an input widget

- What microflow expressions consist of

- How to write microflow expressions

- What it means for an object to be in scope of a microflow

- What retrieving data is

- How to do a retrieve by association

- How to analyze errors

- How to use decisions

- How to automatically count objects, such as the total number of registrations

- The difference between stored and calculated attributes

- What object event handlers are and how you can add them to your app

- How to retrieve a list of objects, such as a registration list

Congratulations! Your users are going to be happy with the improvements you made! Move to the next module to learn how you can make sure that all the data that your users can add is consistent and valid!