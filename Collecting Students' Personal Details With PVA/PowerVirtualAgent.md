# Overview 

Microsoft's Power Virtual Agent allows you to create AI Chatbots that can ask and answer questions in seconds without the help of data scientists or developers. You can decide to create your bot and integrate as a standalone web application, share on Microsoft Teams, on your website, on cortana, telegram or slack. 
Using a Power Automate flow connected to your bot, you can collect responses from your users, collate and upload those responses on SharePoint. Love to see how to make this happen. Let's begin! 

# Prerequisites 
Before we begin designing our bot, let's take some time to talk about how it is expected to work. 
Since our bot is designed for collection of information from students, the flow will be like this. 
Bot introduction (Hi, I’m Esther. I can help with membership registration and answer your questions), 
- What can I help you with? (Student registration or make a complaint) 
- Student registration:   - What is your full name? 
- What is your matriculation number? 
- What is your email address? 
- Input your phone number 
- Upload your photograph online and add the link here 
- What month were you born? 
- What day were you born? 
- What year are you graduating? 
- Allow student to see the details of his/her submission: (These are the details you submitted: - Full name, - Matriculation number, - Email address, - Phone number, - Month of birth, - Day of birth, - Year of graduation) 
- Allow student to confirm the submission: Yes/No (If yes, Power Automate pick responses and store on SharePoint) (If no, the bot restarts from step 3) 

# Building your Power Virtual Agents Bot 
Head over to http://aka.ms/TryPVA and sign in with your Microsoft account. Once signed in, you are directed to a page that looks like the image below 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/3dcc25a9-6d4a-4937-8565-a4570ed7f9cb)

First give your bot a name, I named mine Student Solution. Then select the language your bot will speak and click on create. You will be directed to an interface that looks like the image below 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/641e332b-b8ad-4781-b703-0ccb3ba9241d)

On the right navigation bar, click on 'Topics'. The next page you are directed to has 12 existing topics. 
A topic defines a how a bot conversation plays out. In this sample, we would create new topics from scratch. Topics have trigger phrases — these could be phrases, keywords, or questions that a user is likely to type. We also have conversation nodes — these are what you use to define how a bot should respond and what it should do. 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/b03986d6-b29e-48ad-8a30-dc623902ab41)

Delete the first 4 topics or toggle it off. To delete, go to the topic, select the three horizontal which shows more actions and select delete. After deleting the topics, you would be left with 8 existing topics. 

We are going to create two new topics for this solution, one for **Student Registration** and the other **Student Complaint**, then redirect these newly created topics from the Greeting Topic. 

Now let’s create the first topic. On that same page, click on '+ New topic' at the top. Give your topic a name. I would name mine "Student Registration". 
In the section 'Trigger Phrases', I would input 3 phrases that the student may likely use to start the conversation. 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/673b06ce-416e-491c-aa45-e516347681ed)

Add a simple message which we will delete later. 

Go ahead and create the Second Topic, like the first. I will name mine “Make a Complaint”, add the trigger phrases and finally add a message. 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/4c58ce92-fc14-4880-aa36-2f51ab038bdc)

Save every change you make by clicking on the folder icon at the top right hand of the page. 

Now we are done creating the 2 new topics, let’s go ahead and edit the Greeting topic. 

Go to Topics, select Greeting, leave the trigger phrases. Edit the message node to your welcome message. We can delete the other message node, by clicking on the 3 horizontal dots and select delete. 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/bc8e7831-d192-41fc-af00-4f7e97f64541)

I have edited the message node to show my welcome message when someone interacts with the bot for the first time. 

Hi, I’m Esther. I can help with membership registration and answer your questions. 

Next, add another node by clicking the '+' icon and select “Ask a question”. We need to ask the students if they want to either register or make a complaint. 

Fill in the details correctly. 

-	Ask a question: The question we need to ask, “what Can I help you with?’ 
-	Identity: Since we have 2 options, select Multiple Choice Option 
-	Option for user: We add the first option, “Student Registration” and click on the “+” “new option” to add the second option “Make a Complaint” 
-	Save response as:  It is important we rename our bot variable for each question, so it's easy to reuse. Click on the pencil icon and in the column that pops out by the side, change the bot’s variable name for this question to Helpdesk.

Bot variables are global variables as they are used to store information that do not change from topic to topic. 

Notice that beneath the question block, condition blocks have been added. A separate condition block was created for each option as shown in the image below. 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/fc4039f2-30db-45e5-a42d-ab7adb5c4b46)

Set the conditions to the option. click on the “+” icon and select redirect to another topic and select the topic which the Helpdesk is equal to. 
 
![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/6126abec-a57f-4c34-aa95-b3e95633c06e)

Now we have are done with the Greeting topic, go ahead and save it. 

If the student selects either “Student Registration” or “Make a Complaint” it redirects to that topic. 

Our focus for now will be on Student Registration. Let’s head over to Topics, click on Student Registration and let’s build our bot.

Click on the “+” node and select ask the question, fill in the details correctly. 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/a450b34e-999b-49f3-9622-c0b8b22fbd49)

Click on the “+” node and select ask questions, go ahead, and ask the second and third question, fill in the details correctly and save.

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/7d6333ad-204b-47d4-9ea4-3540787862af)

Do the same for the fourth, fifth and sixth question, fill in the details correctly and save 
 
![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/bc3f6603-7095-4b92-a0d5-c6066a19f564)

 
After collecting all the responses, we want our bot to show the response collected, to the student for errors or correction before submission.  

Click on the “+” node and select show a message.  

These are the details you submitted: Full name – {x}fullNameText. 

To get the exact response for each question, select the “{x}”, a dropdown menu will be show, select the variable name you saved the response as. Do the same for other response. 
 
 ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/74a125c6-458f-4c11-b366-e66e38abd56f)

 After showing the response, we want to ask the student if s/he wants to submit 

Click on the “+” node and select ask question 

Fill in the details correctly. 
-	Ask a question: The question we need to ask, “Do you want to submit now?’ 
-	Identity: Since this is a No/yes question, choose Boolean, notice the nested three blocks that follows next. Go ahead and set the value of the first block to “true” and the second block set to “false”. 
-	Save response as:  It is important we rename our bot variable for each question, so it's easy to reuse. Click on the pencil icon and in the column that pops out by the side, change the bot’s variable name for this question to Helpdesk. Bot variables are global variables as they are used to store information that do not change from topic to topic. 
 
If the student selects yes, the automate is triggered and the information is saved. 

Else if the student selects no, it takes the student back to the third step, which is “what is your name?”. 

Now we need to connect the second condition block to the first question. We do this so that whenever the response to the submit details question is No, it goes back to the first question. To do this, click on the '+' sign and instead of adding a node, click on the small circle, draw, and connect to the first question block. Your flow should look like the image below. 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/9ff0b45a-9e59-408d-a9ea-4f703c0051b3)


You can test your bot to make sure it's working well by clicking 'Test your bot' on the left side of the page.

----------------------------------------------------------------------------
[EDIT REQUIRED Now we need to store details in sharpeoint. for thus head over to storing details.md file
----------------------------------------------------------------------------


Back to the power Virtual Agent(Chatbot) playground. Till now, we have collected all the details from the student and stored the details in the sharepoint list through power automate.

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/07b72a22-aa87-4498-aa77-0e458a9da57c)

 Once the details are successfully submitted to the sharepoint, a message is displayed in the chatbot saying so along with the next steps that the student needs to follow. 
 
![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/250ff663-4e36-45bb-897e-d808099dc082)










