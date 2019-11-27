# Ensuring your Data is Valid and Consistent

## The Importance of Having Valid and Consistent Data

Currently it isn’t possible to delete data at all, so that needs to be built as well. Jimmy should at least be able to delete training events. But what should happen when data is deleted from the app? This is called delete behavior.

If you don’t set up the delete behavior correctly, you run the risk of data being deleted when it shouldn’t, which could cause major problems for Jimmy. Another risk of not having delete behavior set up correctly is that when data is deleted, other objects with a connection to this data become meaningless. In this case they should also be deleted automatically, to keep the database clean.

Think about the following questions:

- Should it be possible for training event to be deleted when people have already registered for it?

- What should happen to a trainee’s registrations if the trainee is deleted?

## Validation Rules
You’ve already built an app with a Domain Model and some pages. Jimmy can add teachers, locations, courses, and trainees. He can even schedule training events and register trainees for them. You should have a set of sample data to work with. But how do you keep that data consistent and make sure there is no missing data? That’s where adding validation to your application becomes important.



###  Add Validation Rules
Validation rules are conditions that should be met before an object is stored in the database. They are placed on the attributes in the Domain Model. When you add a validation rule, you can also enter a custom error message that will be shown when the validation rule is not matched.

The Domain Model is not the only place you can add validations, you can also add validation to microflows and on pages.

- Adding validation to the **Domain Model** means that every component, page, or microflow in your project using that object must pass the validation check. If you apply validation here, it’s applied everywhere

- Adding validation to **microflows** makes the validation rules more accessible and visible for everyone. Those rules are also easily updated without impacting the underlying domain model.

- Adding validation to **pages** only applies on that page, not in other places. Also you can only have one validation rule per field. So a course title can’t be both required and unique if you use a page validation.

### Types of Validation Rules
There are several types of validation rules that you can apply to attributes in the Domain Model:

**Required**
- The attribute needs to have a value. It cannot be empty.
- For example: The description of a course can't be empty.

**Uniq**
- The attribute should have a value that is unique compared to the values of this attribute in all other objects of the same entity.
- For example: A course cannot have the same title as another course which is in the database already.

**Equa**
- The attribute value needs to be equal to a specified value or equal to the value of another attribute of the same object.
- For example: When you have a form to change your password and you need to enter your new password twice.

**Ran**
- The attribute value needs to be in a range between specified values or between the values of other attributes of the same object.
- For example: The duration of a course needs to be a minimum of 1 day, but 10 days at the most.

**Regular expression**
- The attribute needs to match a regular expression. A regular expression uses pattern recognition to check values.
- For example: The email address needs to be a valid email address (something@something.com).

**Maximum length**
- The attribute may have no more than the specified number of characters.
- For example: An American zip code always has five characters, so when someone enters a zip code, the maximum length of that value is five.




What Happens when an Object isn’t Valid?
So, what happens if the object doesn't pass the validation check? Well, depending on where in the app the validation was triggered there are three possible results:

- **Page, with an input widget for the attribute:** The end-user tried to add an object to the database, using a page that has an input widget for the attribute, but did not fill it out correctly. In that case an error message appears underneath the input widget.

- **Page, without an input widget for the attribute:** The end-user tried to add an object to the database, but the attribute that didn't pass the check doesn't have an input widget on the page the end-user is currently looking at. A pop-up message appears, with the error message in it.

- **Microflow: A microflow attempts to commit** the object to the database. In that case an error message appears in the log.

In each of the above cases the object is not committed to the database, preventing incomplete or wrong information from ending up in the database.

### Add Validation Rules to the Domain Model
Time to add validation rules to your Domain Model! Set the following story to Running: **As an administrator, I want data to be valid and consistent, so my database doesn’t become messy**.

Jimmy came up with the following validation rules for the LearnNow app:

![Validation Rules Domain Model 1](/data-validation/images/validation_rules_domain_model_1.png "Validation Rules Domain Model 1")

Let’s start by adding the first validation rule to the Course entity! The validation rule is that Title is Required. That means that a Course can be stored in the Database if an only if it has a title!

1. Open the Domain Model and double click on the Course entity to open its properties.

2. The third tab is the **Validation rules** tab. Click it.

3. Let's add the first validation rule: the title can't be empty. Click **New** to create a new validation rule.

4. Set the **Attribute** to **Title**, because this is the attribute you are creating a validation rule for. The **Rule** is already on **Required**, so that can stay the same.

5. Type a clear error message in the **Error message** text area.

6. Once you're done click **OK**.

![Validation Rules Domain Model 2](/data-validation/images/validation_rules_domain_model_2.png "Validation Rules Domain Model 2")

According to the second validation rule, the title also needs to be unique. This means the same title can't already be in the database. To add this second validation rule to the title attribute, you need to create a new validation rule.

7. Click New to add the second validation rule to the title attribute.

8. Keep going until you've added all validation rules to the Course entity. Here is an overview of them:

![Validation Rules Domain Model 3](/data-validation/images/validation_rules_domain_model_3.png "Validation Rules Domain Model 3")

9. Add the following validation rules to the Location entity as well.

![Validation Rules Domain Model 4](/data-validation/images/validation_rules_domain_model_4.png "Validation Rules Domain Model 4")

## Regular Expressions
### Tip
You don't have to know how to write Regular Expressions, because this can be quite challenging. Just use your favorite search engine and look for Regex and then the thing you want to validate. Regex is the abbreviation for Regular Expression. For example: Regex Email.
## Add Regular Expressions
Now let's add that email address validation rule!

1. Open the properties of the Teacher entity and go to the **Validation rules** tab.

2. Create a new validation rule for the EmailAddress attribute.

3. Set the **Rule** to **Regular expression**.

4. Click **Select** to select the Regular Expression. You don't have one in your app yet, so click **New** to create one right now.

5. Name it **Email** and click **OK**. The following screen opens:

![Add Regular Expressions 1](/data-validation/images/add_regex_1.png "Add Regular Expressions 1")

6. Add the Regular Expression to the **Expression** text area. You can just use your favorite search engine to find regular expressions!

```
(?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|"(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21\x23-\x5b\x5d-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])*")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\[(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?|[a-z0-9-]*[a-z0-9]:(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21-\x5a\x53-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])+)\])
```
7. You want other developers to be able to understand what the expression does, so add a note to the **Documentation** text area. You should say what the Regular Expression checks (and maybe what it doesn't check) and if you found it online, where you found it.

8. Continue until you have created all validation rules for teachers and trainees. Here is an overview of the validation rules:

![Add Regular Expressions 2](/data-validation/images/add_regex_2.png "Add Regular Expressions 2")

Take a look at your Domain Model. Do you see the green checkmarks that have appeared behind the attribute names? This tells you that an attribute has one or more validation rules applied to it.

![Add Regular Expressions 3](/data-validation/images/add_regex_3.png "Add Regular Expressions 3")

You are probably wondering why you didn't have to add any validation rules to the TrainingEvent entity yet. Go to the next lecture to discover why that is.

## Validation in Microflows
In the previous lecture you added validation rules to the Domain Model. You did that for the following entities: Course, Location, Teacher, Trainee. The TrainingEvent also needed validation rules, but you didn't add these to the Domain Model. Let's take a look at those validation rules again:

 ![Validation Microflows 1](/data-validation/images/validation_microflows_1.png "Validation Microflows 1")

Here you see that four validations are required. One of them is an attribute (StartDate), the other three are associations. Unlike attributes, associations can't be validated in the Domain Model. You need to do that either on the page or in a microflow. A microflow is the preferred option here. This is because it's more future-proof than page-based validation, because it allows your app to scale more easily.

Maybe you are wondering right now why you didn't add the StartDate validation to the Domain Model earlier. This is because your end-user only expects to have their actions validated once. For example:  say for a particular entity you validate some information in the Domain Model and some in a microflow, the-end user will have validation messages popping up at different times. This is very confusing and frustrating for your end-user. So: the minute you validate one member (attribute or association) of an entity in a microflow, do all the other validations in that microflow at the same time.

Now you know that you are going to have to build a microflow for the validation process, it's time to figure out when this microflow should be triggered. You have two options:

- A **before commit** object event handler on the TrainingEvent entity in the Domain Model.

- A **custom save** button on the TrainingEvent_NewEdit page.

The question you should ask yourself is: does the TrainingEvent need to be validated before going to the database (object event handler) or when the end-user interacts with the information inside the TrainingEvent (custom save button)?

The easiest solution would be to create an object event handler. However, in the previous module you created the functionality to store the total number of registrations in the TrainingEvent. This microflow (ACO_ADE_Registration_SetTotalNumberOfRegistrations) does a commit of the TrainingEvent object. This commit will also trigger the validation process if you add it as an object event handler. In this case, this isn't desirable because you don't need to validate the TrainingEvent when storing the total number of registrations. For this reason it is better to create a custom save button on the TrainingEvent_NewEdit page that validates the TrainingEvent before storing it in the database.

Before you get to work, let's take a look at the desired end goal: The TrainingEvent_NewEdit page, with specific validation feedback message underneath each input widget. Also: all validation feedback messages are presented to the end-user in one go.

 ![Validation Microflows 2](/data-validation/images/validation_microflows_2.png "Validation Microflows 2")

Let's break that down:

The StartDate, Course, Location and Teacher need to become required fields. They can't be empty. You don’t have to worry about the EndDate, because that field will be filled automatically.

Each input widget (field) should get its own validation feedback message, shown underneath the input widget. If you do this, the user will know which field they still need to fill in and with what information.

All these validation feedback messages need to be presented to the end-user at once, so they don’t get frustrated with multiple rounds of feedback messages.

Only when the TrainingEvent passes all validation checks can the TrainingEvent be committed to the database (the user can save the training event).

After the TrainingEvent is committed (the training event is saved), the page needs to be closed. This will make the app go back to the TrainingEvent_Overview page. If this doesn't happen the end-user will be confused, as they will think the training event hasn’t been saved! The overview page also needs to be refreshed to show the new TrainingEvent information.

To complete all that, you need to create a microflow that will be triggered from the Save button, add the validation checks, and make sure that feedback messages appear! You will see how you can do all that in the following assignments!

### Create a Validation Microflow
Firstly, you need to create a microflow that will be triggered from the Save button. Here is how you do it:

1. Open the TrainingEvent_NewEdit page. This is a page with a data view that is connected to the TrainingEvent entity. In the **footer** of the dataview, you will find the default **Save** and **Cancel** buttons. Right click the **Save** button that is indicated below and click **Edit on click action**.


 ![Create Validation Microflow 1](/data-validation/images/create_validation_microflow_1.png "Create Validation Microflow 1")

2. Change the **On click** from Save changes to **Call a microflow**.

3. The microflow you need does not exist yet, so in the next screen click **New**. A good name for this microflow would be **ACT_TrainingEvent_Save**. Complete the creation of the microflow and open it.

The microflow has an input parameter of TrainingEvent. This is the TrainingEvent that is about to be stored in the database. But before it is allowed to be committed to the database, it first needs to pass the validation checks!

4. As always, start with the end result. That would be committing the TrainingEvent and closing the page. Add these two activities to your microflow. Don't forget to set **Refresh to Client** to **yes**, as you want to have a relevant message appearing once the checks performed in the microflow are done.

Here is what the microflow will look like at the end of this assignment:

 ![Create Validation Microflow 2](/data-validation/images/create_validation_microflow_2.png "Create Validation Microflow 2")

So far, you made the Save button trigger a simple microflow. The microflow you created doesn’t include any validation checks yet. See how you can build those checks in the following assignment!

### Build Validation Checks
Approach the rest of this assignment step by step. Firstly, build all the necessary checks. After that add the validation feedback messages to the members that are being checked. Once you've done that successfully make sure to get all feedback messages back to the end-user in one go.

You already know how to build checks: by using decisions. You can check all fields in one decision, by using the following microflow expression:

$TrainingEvent/StartDate != empty **AND**
$TrainingEvent/MyFirstModule.TrainingEvent_Course != empty **AND**
$TrainingEvent/MyFirstModule.TrainingEvent_Location != empty **AND**
$TrainingEvent/MyFirstModule.TrainingEvent_Teacher != empty

However, there are two issues with this approach:

1. It does nothing for the readability of the microflow. The microflow actually becomes more difficult to interpret, because you have to open the decision to see what it does exactly. You also need to read and interpret a couple of lines of microflow expression. This is something you should try to avoid.

2. If you do all checks in one decision, it becomes impossible to add the validation feedback messages underneath the specific input widgets. This is because you can't differentiate between which fields have and have not passed the validation. To achieve this, you need to build a decision per input widget.

Add the four decisions to your microflow. Make sure to add a clear caption and to follow the 'happy path'. In other words: make sure that the outgoing **true** flow is the one that goes on to the commit activity and the **false** flow goes to an end event. In the next lecture you will see how you can change these end events to feedback messages.

Here is how your microflow should look like by the end of this assignment:

 ![Build Validation Checks](/data-validation/images/build_validation_checks.png "Build Validation Checks")

### Add Validation Feedback Messages
The next step is to add the validation feedback messages. These let the end-user know a validation check hasn’t passed: when the microflow travels down a false path. To add the validation feedback messages to your microflow:

1. Add an activity to the first false flow (the one coming out of the decision that checks the StartDate).

2. Set the type of action to **Validation feedback**. The following pop-up will appear:

- The **Variable** is the object you are validating (in this case the **TrainingEvent**).

- The **Member** is the input widget you want the validation message to appear underneath. In this case the **StartDate**.

- The **Template** is the message that will be shown to the end-user. Fill out a message that will help your users understand what they need to do. In this case “Please select a start date”.

![Validation Feedback Message 1](/data-validation/images/validation_feedback_message_1.png "Validation Feedback Message 1")

3. Click **OK**.

4. Repeat the previous steps to add validation feedback activities to each outgoing false flow and set them up correctly.

At the end of this assignment, your microflow should look like this:

![Validation Feedback Message 2](/data-validation/images/validation_feedback_message_2.png "Validation Feedback Message 2")


At this point the end-user will get multiple rounds of feedback. Because every time a check doesn't pass, the microflow goes down the false path and the app exits the microflow (via the end event). It never reaches the next check! This behavior is very frustrating for the end-user. You need to make sure that all checks are executed at once and the end-user immediately sees what they still need to do to be able to save their training event. What you need is a way to go through all the checks, even if the microflow goes down a false path. Learn more about how you can do that in the next assignment!

### Merge Multiple Flows
A decision can only have one incoming flow. This means you can't directly make the false flow continue to the next decision. There is a component you can use for this though: the **merge**.

The merge is the red diamond shaped component in microflows. It's used to go from multiple flows back to one single flow.

![Merge Multiple Flows 1](/data-validation/images/merge_multiple_flows_1.png "Merge Multiple Flows 1")

Here is what you need to do to the microflow:

1. Delete the **end events** at the bottom of each false path.

2. Add a **merge** after each decision.

3. Drag a flow from the validation feedback activities to the merges, just like in the next image.

![Merge Multiple Flows 2](/data-validation/images/merge_multiple_flows_2.png "Merge Multiple Flows 2")

Can you predict what the problem is with the microflow at its current state? If you're not sure, try running your app and test the functionality.

The problem with the current solution is that even though the microflow goes through all the checks, it will still commit the TrainingEvent. Even if it isn't valid. So how can you still maintain one flow, where you give all feedback messages back at once, without committing the object at the end if it isn't valid? You need a way to record whether somewhere in the process, the microflow went down a false path. In other words: you need to create a **flag**. A flag is a term for a true/false condition. It signals a go/no go condition, like a railroad flagman indicating whether or not it's safe for the train to proceed.

This true/false flag sounds an awful lot like an attribute type you already know, doesn't it? That's right, it's a **boolean** value! And the flag is just like a **variable** that you can use to store that boolean value.

Let’s continue with the assignment and add a flag to the microflow! The starting value of this flag will be true. This is because you assume that the end-user did what they were supposed to do, which is fill out every field of the form. If they didn't do that – causing the microflow to travel down the false path – the value of the Boolean variable will be set to **false**.

4. Place an activity at the beginning of the microflow, directly after the start event.

5. Set the type of action to **Create variable** and set the value to **true**.

![Merge Multiple Flows 3](/data-validation/images/merge_multiple_flows_3.png "Merge Multiple Flows 3")

6. Place an activity on the **false** path for all four decisions.

Repeat these three steps above for all four newly created activities.

- Set the activity type to **Change variable**.

- elect the **ValidTrainingEvent** variable.

- Set the value to **false**.

![Merge Multiple Flows 4](/data-validation/images/merge_multiple_flows_4.png "Merge Multiple Flows 4")

7. At the end of the validation checks, right before the microflow does the commit, you place a decision. This decision will check whether the value of the Boolean variable is still true.

- If yes, the TrainingEvent object passes all validation checks and can be committed.

- If not, you know that one or more checks didn't pass and the microflow needs to exit without committing the object. At that point the end-user will be presented with the validation feedback messages.

![Merge Multiple Flows 5](/data-validation/images/merge_multiple_flows_5.png "Merge Multiple Flows 5")

Here is what your microflow will look like at the end of this assignment:

![Merge Multiple Flows 6](/data-validation/images/merge_multiple_flows_6.png "Merge Multiple Flows 6")

Run your app and test the functionality. Does it work as expected? If not, go through this module again to see if you followed the instructions step by step. If yes, go ahead and commit your work to the Team Server and set the story to Done.

## Deleting Objects
So far in this module, you have learned how to make sure that the data that enters your database is consistent and valid. In the same way, you need to make sure you have control over what data is deleted from your database!

In the Developer Portal, set the next user story to running: **As an administrator, I want to be able to delete training events that don’t have registrations, so I can’t accidentally delete a training event that people have already paid for to attend**.



According to that user story, Jimmy wants to be able to delete training events, but only if no one has registered for that event yet. Otherwise he could get some unhappy faces, if trainees have already paid to attend a certain training event and then the event was canceled all of a sudden. Or trainees would show up at the event, but of course there would be no training because the event had been canceled.

Therefore, you need to make sure that when the user deletes an object, the associated objects do not get deleted as well. The following image is an example showing you what you will need to decide on:

![Delete Objects](/data-validation/images/delete_objects.png "Delete Objects")

The first section, **multiplicity**, shows you what type an association is.

The next two options show you the delete behavior settings. In other words, what should happen when you delete one of the associated objects. In the example, when you want to delete the ‘TrainingEvent’ object, you have three options:

- **Keep ‘Registration’ object(s)**. This means that you will be able to delete the training event and all the registrations that belong to it will stay in the system. This is also called no predefinition and is the default setting for delete behavior.

- **Delete ‘Registration’ object(s) as well**. This means the training event and all registrations that belong to it will be deleted from the system.

- **Delete ‘TrainingEvent’ object only if it is not associated with ‘Registration’ object(s)**. This means that the training event can only be deleted if it doesn’t have any registrations connected to it yet. This type of delete behavior is called prevention of delete. When selecting this, you also get the option to show an error message to the end-user, informing them why they cannot delete a certain object.

#### Tip

If you get a system error message when you try to delete an object in an app, take a look at your Domain Model. Perhaps somewhere down the line prevention of delete is triggered and you forgot to fill out a custom error message.

### Add Delete Button
Firstly, let’s make sure that there is a delete button in place. Jimmy wants to be able to delete training events, so it is a good idea to add the delete button to the TrainingEvent_Overview page.

To do that:

1. Open the **TrainingEvent_Overview** page in Mendix Studio Pro.

2. In the **Toolbox**, look for the **Delete button**.

3. Place it in the list view item, to the right of the **Details** button. You can do that by dragging and dropping it underneath the Details button, in the area that’s highlighted in the next image.

![Add Delete Button 1](/data-validation/images/add_delete_button_1.png "Add Delete Button 1")

4. The button is now placed next to the existing button. Double click the button to open its properties. Empty the caption and select the **trash** icon. Set the button style to **Danger** so it gets a red color.

![Add Delete Button 2](/data-validation/images/add_delete_button_2.png "Add Delete Button 2")

5. Set **Close page** to **No**. That means that the TrainingEvent Overview page will stay open when you delete a training event.

6. Click **OK**.

Well done! You set up the **Delete button** that will delete a training event. Continue to the next assignment to configure the delete behavior. You will prevent Training Events to be deleted if some participants have already registered for those events!

### Add Delete Behavior: Prevention of Delete
Awesome, the button is done! Now it’s time to set up the delete behavior. Jimmy wants training events to be deleted only when there aren’t any registrations connected to them yet.

1. You manage delete behavior in the **Domain Model**, so go ahead and open it.

2. Double click on the **Registration_TrainingEvent** association to open its properties. The following window will open:

![Add Delete Behavior 1](/data-validation/images/add_delete_behavior_1.png "Add Delete Behavior 1")

3. Under **On delete of ‘TrainingEvent’** select **Delete ‘TrainingEvent’ object only if it is not associated with ‘Registration’ object(s)**. Leave the other options as they are set by default.

4. Add an error message in the text area which appears under **Delete ‘TrainingEvent’ object only if it is not associated with ‘Registration’ object(s)**. This error message is shown to the end-user when the deletion is prevented. Perhaps something like this: **Sorry, this training event can't be deleted. People have already registered for it!**

5. Click **OK**.

Do you see that blue border that has appeared around the association? This tells you that this association has **prevention of delete** applied to it.

![Add Delete Behavior 2](/data-validation/images/add_delete_behavior_2.png "Add Delete Behavior 2")

6. Congratulations! Jimmy can now cancel scheduled training events. He will be really happy with that! **Commit** your newly created functionality to the Team Server and set the story to **Done**. Don’t forget to select the story as the related user story during the commit!

## Cascading Delete
Another thing that Jimmy wants to be able to delete is the Trainees and their information from the system. When they are deleted, all the registrations that belong to them should be deleted as well. This type of delete behavior is called **cascading delete**. That means that when one object is deleted, all the associated objects are deleted automatically as well. You can see whether an association has **cascading delete** applied to it by the red border that appears around the association (as shown in the image below).

![Cascading Delete](/data-validation/images/cascading_delete.png "Cascading Delete")

### Delete Objects with Cascading Delete
Can you build this functionality completely by yourself using the same approach as in the previous assignments? Here are the steps that you will need to take:

1. Set the next user story to Running: **As an administrator, I want to be able to delete Trainees and all their Registrations, so that I can remove them from the system if they no longer wish to be a LearnNow student.**

Add a **Delete button** on the **Trainee_Overview** page. Make the button stand out by giving it a nice icon and colour. If you need help with that step you can refer to lecture '8.5.1 Add Delete button'. Here is what your button should look like at the end:

![Delete Objects with Cascading Delete 1](/data-validation/images/delete_objects_cascading_delete_1.png "Delete Objects with Cascading Delete 1")

3. Add the delete behaviour on the **Registration_Trainee** association in the Domain Model. If you need help with that step you can refer to lecture '8.5.2 Add Delete Behaviour: Prevention of Delete'. Note that you need to select **Delete 'Registration'Object(s) as well** this time!

![Delete Objects with Cascading Delete 2](/data-validation/images/delete_objects_cascading_delete_2.png "Delete Objects with Cascading Delete 2")

4. Make sure to run and test your solution! Once you are satisfied with it, **Commit** your work to the Team Server and set the story to **Done**!

Congratulations! You have managed to make sure that the data in your database is always consistent and valid! In the next lecture you will learn how to set up the security of your app. In that way, your data will not only be correct, but will also be safe!

## Summary
Congratulations! You now have an app that is not only user friendly and effective, but also makes sure that the data that gets in or out of your data base is consistent and valid!

In more detail, in this lecture you learned:

- What validation rules are and how to add them to your Domain Model

- What regular expressions are and how to use them

- How to create validation microflows

- How to provide your users with useful feedback messages

- How to prevent your users from deleting data that they shouldn’t

- How to automate the deletion of data that is redundant

In the next lecture you will learn how to set up the security of your app. In that way, your data will not only be correct, but will also be safe!