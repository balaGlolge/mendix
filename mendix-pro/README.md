# Mendix Studio Pro
![Layout Mendix Studio Pro](/mendix-pro/images/pro_layout.png "Layout Mendix Studio Pro")

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

![Working Copy](/mendix-pro/images/working_copy.png "Working Copy")

## Status and Changes
Different kinds of changes are visualized with the following icons:
![Status Changes](/mendix-pro/images/working_copy.png "Working Copy")

## Committing Changes
Sending changes to the repository is called committing. The idea is that you commit small, consistent pieces of work to the repository (for example, implementing a new feature and fixing a bug).

Mendix Studio Pro also attaches some information automatically:
- The author (the user who committed)
- The date and time of the commit
- The list of changed content (documents/folder/modules), along with the type of the change (modify, add, delete, etc.)
- The version of Mendix Studio Pro that was used to commit

## Update
Committing is only possible when your working copy is up to date with the repository. If someone else committed a change since the last time you updated, you have to update first.