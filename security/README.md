# Securing your App
## What Needs to Be Secured?
In Mendix, you add security to three things: pages, microflows, and data (entities). This is called access. You either have access to a page or you don't. If you don't have access to a certain page, you automatically won't see buttons or navigation items that go to that page. The same goes for microflows: if you don't have access to a microflow, you won't see the buttons that trigger this microflow. If you don't have create rights for a certain entity, you won't see the Add buttons in the app.

You manage security in two places: Project security and Module security**. **Project security** is where you set the security level and where you manage overall security settings. **Module security** is where you set up the page, microflow, and entity access.



Security Levels
Mendix apps have three security levels:

Off: there is no security in place. Anyone can use the app and you don't have to log in to do so. This is the default setting when you start developing your app.

Prototype/Demo: this level requires you to set up the Page access and the Microflow access. In other words, you define who can visit what page and who can trigger which microflow. This security level is really useful for quickly checking (or demoing) your security. What does the app look like for a particular user?

Production: this is where you configure the Entity access. Here you determine whether someone can create objects (like a training event) and whether they can delete objects. This also determines whether you can see the information inside an object. And last but not least whether you can change the information inside an object.

You are currently building a free app, which means it’s not connected to a Mendix license. These apps can run in the cloud without security being turned on. For licensed apps this works a little bit differently though. If you want to push a licensed app to an environment (this is the version of the app that the end-users use), you need to have Production security on and completely configured!

## User and Module Roles
The first thing you need to do when it comes to security is decide on the user roles. What are the different types of users for your app? For the LearnNow TrainingManagement app that would be:

- Administrators (in this case only Jimmy)

- Teachers

- Trainees

In the future the LearnNow app may be extended with an **Invoicing** module, that handles all invoices and payments. In this case, you will also need to extend the user roles with the **Finance** user role, with its own module role in the **Invoicing** module. The module will be off limits for all other users!

Each user role gets their own set of access rights. An administrator should be able to create, edit, and delete courses and training events for example. Trainees should only be able to see the existing training events and details of the course. What should teachers be able to see and do?

These access rights are managed in the **Module security**. Per module you can create **module roles** that capture everything a certain user can and can't do in a particular module. These module roles are connected to user roles. If a particular user role doesn't have a module role for a certain module, the entire module is automatically off limits. That user won't be able to visit the pages that belong to the module, trigger the microflows or see the data and interact with it. User roles function as a sort of umbrella for the module roles.

A typical user role has the module role **User** in the **System** and the **Administration** modules. Roles in other models depend on the function of the user.

![User and Module Roles](/security/images/user_module_roles.png "User and Module Roles")

End-users users will only see/use the user roles and not the module roles. User roles can be assigned to end-users. Module roles are assigned to user roles, which is done at the project level.

The purpose of the distinction between user roles and module roles is to make a module self-contained and independent from the project in which it is defined or used. The modules can be reused in different projects and can be published to the Mendix App Store.

Users can have more than one user role in an app. But during this learning path you will only give users one user role.

### Setup Project Security Level
Time to set up the user roles for the LearnNow app!

1. Set the story to **Running**: As an Administrator, I want the app to be secure, so I comply with the rules of data protection.

2. In Mendix Studio Pro, open the **Project Security** pop-up window by double-clicking the security icon. You can find it in the **Project Explorer**, at the top.

![Setup Project Security 1](/security/images/setup_project_security_1.png "Setup Project Security 1")

3. Set the security level to **Prototype/Demo**. The window changes immediately and shows all the security settings you can manage. Keep the window open.

![Setup Project Security 2](/security/images/setup_project_security_2.png "Setup Project Security 2")

The first tab is the **Module status** tab. Here you can see the security status of your module(s). As long as there are still columns on incomplete, you aren't finished with configuring security!


Note: If you started your project in Mendix Studio Pro, then your entity access will have been configured already. For the purpose of this exercise, you need to remove this configuration.

- Set security from Prototype/Demo to Production and click Edit module security.

- Go to the Entity access tab and if there are any entries in the entities – remove all the lines for the six entities. To do that, select all of them and click Delete.

- Click OK and set security back to Prototype/Demo.

4. Also, take a look at the **Errors** pane, you should have a number of errors all of a sudden!

![Setup Project Security 3](/security/images/setup_project_security_3.png "Setup Project Security 3")

Because you have set the security level to Prototype/Demo, you now get an error for every page and microflow that is accessible in the client. In other words: every page and microflow that is connected to a button or navigation item will give you an error because the app doesn't know which users are allowed to use them. When you configure page and microflow access, the errors will disappear again.

### Create Module Roles
Open the **Module security** for the MyFirstModule by double clicking the security icon that has just appeared underneath the **Domain Model**. The module security window has four tabs: **Module roles, Page access, Nanoflow access, Microflow access.**

Let's start with defining the module roles you need: Administrator, Teacher, and Trainee. Rename the **User** module role to **Teacher** and create a new module role for the **Administrator** and **Trainee**.

![Create Module Roles](/security/images/create_module_roles.png "Create Module Roles")

3. Click **OK** to close the **Module Security** window.

## Access Rules
Module security is where you determine who gets to do what. You do this by configuring the **Page**, **Microflow**, and **Entity access**.

![Access Rules](/security/images/access_rules.png "Access Rules")

### Page Access
- **Page access** defines which pages can be accessed. The navigation items (menu bars/buttons) will show items only if access is granted.

- **Page access** takes a shape of a matrix showing pages and modules roles. For each combination, you can indicate if the module role has access to the page. You can also edit this information in a page using the **Visible for** property.

Note that this configuration is only applied to public pages when they are opened directly from the client. A page that is opened by a microflow will only open if the role is allowed to execute the microflow.

### Microflow Access
- **Microflow access** defines which microflows can be used. The navigation items (menu bars/buttons) will show items only if access is granted.

- **Microflow access** also uses a matrix to show microflows and modules roles. For each combination you can indicate if the module role has access to the microflow. You can also edit this information in a microflow using the **Allowed roles** property.

Note that these access settings are only checked when the microflow is executed from the client. A microflow called as a sub-microflow, or a microflow set as an event handler, is allowed if the user has access to the calling microflow or if the related entity event is allowed for the user.

### Entity Access
- **Entity access** defines for each module role whether users are authorized to **Create**, **Read**, **Update**, and **Delete** (CRUD) objects of the entity. Read means whether you can see the information, **Update** whether you can change it.

-  **Entity access** is configured with access rules that are applied to entities. Each access rule in turn is applied to one or more module roles.

- The access rules of an entity define what a user is allowed to do with objects of that entity. Users can be allowed to create and delete objects, and to view and edit member values. A member is an attribute or association. Furthermore, the set of objects available for viewing, editing and removing can be limited by means of an XPath constraint.

Every access rule is applicable to one or more module roles. The access rule grants certain access rights to those roles. Rules are additive, which means that if multiple access rules apply to the same module role, all access rights of those rules are combined for that module role.

### Set Up Page and Microflow Access
Now let’s take a look at how to configure page and microflow access!

The Administrator (Jimmy) should always have access to all pages and custom logic. The Teacher and the Trainee however don’t need so much and therefore shouldn't have access to everything.

For example:

- The Teacher should be able to see the locations (so they know where they can train), but not edit the details (for data consistency). So, they need access to the Location_Overview page, but not to the Location_NewEdit page.

- Trainees should only be able to see the TrainingEvent_Overview page, so they can check out the agenda. All other pages should be off limits.

- If this is the case, it's probably also a good idea to give the trainee a **Role-based home page** based on the TrainingEvent_Overview page (which we’ll also do below). Having a home page with lots of buttons which the user can’t use is at best a distraction and at worst gives the impression that the app is broken or not well designed.

### Set Up the Page and the Microflow Access
Let’s first set up access for each role:

1. Open the **Module Security** and go to the **Page Access** tab.

2. Use the information in the table below to configure the page access (Y = Yes, has access; N=No, does not have access).

![Page and Microflow Access](/security/images/page_and_microflow_access.png "Page and Microflow Access")

3. Once you've configured the page access, open the **Microflow access** tab:

- Only the Administrator should be able to create, delete, and edit training events.

- The Teacher and the Trainee shouldn't have access to these functionalities.

4. All microflows in the list are related to these functionalities. Give the Administrator access to all of them. Click **OK** to close the **Module Security** window.

### Set Up Entity Access
1. To be able to set up entity access, the first thing you need is to set the security level to **Production** security. If you don't remember how to do this, take a quick look back at lecture 9.3 of this module.

This time you will get even a longer list of errors. This is because for every entity in your domain model you need to say who can **create** or **delete** objects of this entity. And then you need to say who can **read** (see) and **update** (edit) the information per attribute.

2. Open the **Module Security** again. A new tab has appeared: the **Entity access** tab! Open it.

![Setup Entity Access 1](/security/images/setup_entity_access_1.png "Setup Entity Access 1")

#### The Administrator
3. The access rules for the Administrator are easy again: Jimmy should be able to do everything! Click **New** to create the access rules for the Administrator. Select all entities and click **OK**.

![Setup Entity Access 2](/security/images/setup_entity_access_2.png "Setup Entity Access 2")

4. Since Jimmy will have **create**, **delete**, **read** and **update** access everywhere, you can set the rules up for all entities at once. Select the **Administrator** role. Also check **Allow creating new objects** and **Allow deleting existing objects**. Set the **Member read and write rights** to **Read**, **Write**. Click **OK**.

![Setup Entity Access 3](/security/images/setup_entity_access_3.png "Setup Entity Access 3")

5. In the **Entity access** tab of the **Security** screen you will now see six access rules: one for each entity. That was a nice little shortcut, wasn't it?

![Setup Entity Access 4](/security/images/setup_entity_access_4.png "Setup Entity Access 4")

#### The Trainer
6. Use the same trick to set up the entity access for the Teacher role. The Teacher **shouldn't be allowed to create any objects, neither should he be allowed to delete them**. For the information inside the attributes. The Trainer should be able to see (**read**) all the information, but not change (**write**) it.

![Setup Entity Access 5](/security/images/setup_entity_access_5.png "Setup Entity Access 5")

7. After adding, this is how the Entity access windows should look like:

![Setup Entity Access 6](/security/images/setup_entity_access_6.png "Setup Entity Access 6")

#### The Trainee
8. Last but not least: the Trainee module role. The Trainee should only be able to **read** the information inside the TrainingEvent entity. Nothing else! **Create**, **delete** and **write** is off limits. The total number of registrations should also be hidden from the Trainee.

Click **New** to create a new access rule. Select the TrainingEvent entity. Now you end up at a different screen to define the entity access. Here you can say per attribute what the access should be.

![Setup Entity Access 7](/security/images/setup_entity_access_7.png "Setup Entity Access 7")

This is how the Entity access window should look like now:

![Setup Entity Access 8](/security/images/setup_entity_access_8.png "Setup Entity Access 8")

Take a look at the **Error** pane. There are still four errors left:

![Setup Entity Access 9](/security/images/setup_entity_access_9.png "Setup Entity Access 9")

The first three errors are there because you have given the Trainee read access to the TrainingEvent_Course, TrainingEvent_Location and TrainingEvent_Teacher associations. But you haven't given the Trainee access to the information inside these entities. So to fix these errors the Trainee needs to have **read** access for the attributes that are used to show the selected Course, Location and Teacher. These are respectively: Title, Name, and Address.

8. Go ahead and create these access rules. After this you should now have the following access rules:

![Setup Entity Access 10](/security/images/setup_entity_access_10.png "Setup Entity Access 10")

9. The last error is because you haven't given the Trainee **read** access to the TotalNumberOfRegistrations attribute. But his attribute is shown on a page that the Trainee does have access to. This results in a security conflict! Double click the error to quickly go to the page that the attribute is displayed on. The line where the attribute is displayed is automatically selected.

Now you are going to use **conditional visibility** to hide this entire line from the Trainee. This will fix the error (yay!) but also hide the 'Number of registrations:' part from the Trainee. This line of text isn't very useful for the Trainee anyway, because the Trainee can't see the number that follows after it.

10. Right click the line and click **Edit condition for visible...** Check the **Show the text for selected roles** checkbox and in the options that appear deselect the Trainee. Like this:

![Setup Entity Access 11](/security/images/setup_entity_access_11.png "Setup Entity Access 11")

Finally, click **OK**.

Amazing, all errors are gone! Take a look at your Project Security. Do you see that green dot that says **Complete**? Yes, that's right, the security is now completely configured! Congratulations!

## Project Security User Settings
You’re already familiar with the Project Security settings window from our discussion of the **Module status** and User role tabs earlier in this module. Let’s take a look at some of the other tabs!

### The Administrator Tab
The third tab in the Project Security settings window is the **Administrator** tab. Here you manage the Master Administrator login credentials. For this administrator the name, password, and user role are set.

These are the default settings:

- **Name**: MxAdmin

- **Password**: 1 (only for local deployment)

- **User role**: Administrator

When the application is deployed, a user is created with these credentials. The set password applies only for local deployments, not to the Mendix Cloud. Per environment a strong password for the admin user must be set after deployment. After turning security on you can use the Master Administrator account to login to your app.

### The Demo Users Tab

Tab number four is the **Demo users** tab. You can use demo users to quickly switch user roles in the app. This will allow you to test the security settings for each user role, without constantly having to log out and log in again.

There are already two demo users in place:

- One for the Administrator, named demo_administrator

- One for the Teacher, named demo_user

### The Anonymous Users Tab

The next tab is the **Anonymous users** tab. Here you set whether you want to allow anonymous users to use the app or not. Anonymous users can use the app without logging in. Be careful with this! If you allow anonymous users access to your apps give them their own user role, with very limited access! Otherwise you don't know who might get their hands on your data!

### The Password Policy Tab

The last tab is the **Password policy**. This is where you determine how strict you want to be when it comes to your users' passwords. What is the minimum length? Do they need to have a digit or special character in their password? Does it require mixed case or not? Depending on the type of app you are building – whether the app handles sensitive data or not – you can adjust the password policy to be simple or strict.

### Test Security
The last thing you should do before you can set the story to **Done** and tell Jimmy that the first version of the LearnNow app is ready is check the security!

1. In the **Demo users** tab of the **Project Security** window, add a **new demo user** for the **Trainee** user role. Name it **demo_trainee**, with the user role for trainee selected.

2. Run your app and visit it. You won't go to the homepage now, but to a login page. Use the Master Administrator credentials to log in to the app.

![Test Security 1](/security/images/test_security_1.png "Test Security 1")

3. Check out your application! You can use the user switcher at the right side of the screen to switch to different user roles. If you select the **demo_trainee** user, you will end up on the role-based homepage.

![Test Security 2](/security/images/test_security_2.png "Test Security 2")

4. Commit your work to the Team Server and set the user story to **Done**. Congratulations!

5. Now to truly finish everything also do a cloud run. This will update the cloud version of the app! You can show off the cloud version of the LearnNow app to all your friends and colleagues! Click Run instead of **Run locally** in the top bar of Mendix Studio Pro.

This may take a while, so why don't you go on to the next Module of this Learning Path?

## Summary
Congratulations! You now have an app that is user friendly, effective, consistent, and secure.

You learned a lot of new things in this last module. Here is a short overview of what you learned:

- What data security means and how you can apply it in your app

- What User and Module Roles are and how you can create them

- How you allow only certain users to view or edit your App by setting up Access Rules

- How to configure your Project Security

- How to Test the Security of your app

In the next module, you learn how you can add mobile-specific features to your app and allow your users to access certain pages while there are on the go!
