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
4. Toolbox, Properties, Buzz
5. Preview

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
