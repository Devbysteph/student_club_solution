# Overview of the solution

### Problem Statement
Student Clubs and organizations are currently facing challenges in efficiently managing the process of issuing identification cards(ID Card) to their members. The current process is manual, time-consuming, and requires physical presence, which can be inconvenient for both the club as well as its members. As a result, clubs are looking for a solution that can automate the process of issuing Identification cards and make it more seamless for their members.

This solution aims to address these challenges by automating the process of issuing identity cards to club members. This would eliminate the need for physical presence and make the process more seamless and convenient for members. This solution utilizes Microsoft Power Platform.
This sample showcases how you can use a power virtual agent to collect response from students and upload them in real-time on SharePoint. From SharePoint, you can automate the creation of the ID card with power automate. 

In this sample, we would show you how to build a Chatbot with Power Virtual Agents, upload the response to a share Point site and generate an Identification card using ID Card Template with Power Automate. For this sample we would be using the name “Student Solution” to identify our solution. 

Implementing this solution could have several benefits for clubs and their members. For clubs, it would reduce the time and resources required to issue identity cards, improve data accuracy and security, and provide a more convenient and modern experience for members. For members, it would eliminate the need for physical presence, reduce wait times, and provide a more accessible and user-friendly experience.


# Creating a SharePoint Site
There are two types of SharePoint sites:

- Team site enables team members to create and edit content and collaborate on projects, events, or ideas. They are restricted to people in your Microsoft 365 Group. Each member of the group has the same permissions.

- Communication site is relevant when you need to broadcast a message, tell a story, or share content for viewing to a larger audience in our organization. Behind the scene, just a few members are permitted to create and contribute to the content. In this sample, we would create a Communication Site.

- Head over to https://sharepoint.com and sign in with your Microsoft account.

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/ac2a1adc-4352-480b-97f8-df6d916372f1)

- Click on '+ Create site' and select 'Communication site'.
- Give your site a name and add a description if you wish to at this point. Notice that as you type in the name of your site, it automatically creates a site address and confirms if it is available in your organization. You can also decide to pick another language convenient for you aside from English.
- When completed, click 'Finish'. The result is shown in the image below.
![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/90b9e206-e29b-453c-833c-4707834cf2eb)

# Creating a SharePoint List

- Click on '+ New' and in the dropdown, click on 'List'.
- Click on 'Blank List' and give your SharePoint List a name. If you wish to, you can add a description or decide to leave that for later.
- Once you have completed this, click on 'Create'. You would be redirected to a new page that looks like the one in the image below.

  ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/66179284-c147-4674-a927-31151cf04039)


# Populating our SharePoint List

Now it's time to populate our SharePoint list with the required columns for the solution we are building. But first, let's look at what our solution would look like.

In our solution, we want to store the details of the students in a sharepoint list.

So, following attributes best describe a college student willing to join a club - 

1.	Full Name 
2.	Matriculation Number 
3.	Email Address 
4.	Phone number 
5.	Month and Day of birth 
6.	Year of graduation

The above details are collected from the students using a power virtual agent chatbot.

Our database has to have 6 columns for storing the data collected -  
- To add the first column (Full Name), click on the column 'Title'. Go to 'Column Settings', then 'Rename', and change the name of the column from Title to Full Name. 
- To add a column for each question, click on '+ Add Column', then 'Single Line of Text/Number' according to the value to be fed in that column. 
- In the sidebar that pops out fill in the following details: 
-	Name: Use each detail as to the name of each column. 
-	Click on 'Save' to save the column. 
-	Replicate this process for the other fields. In the end, your SharePoint list should look like the one in the image below.

  ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/bdedc362-1c63-462f-bb1b-d732babf148d)

In addition to the above columns, we define one more column named "PhotoUploaded" which initially contains value 'No' for every entry. More details of this column is given in idCardGeneration.md file.

Now it's time to start developing an interface for our solution!

The first file named 'PowerVirtualAgent.md' elaborates the steps involved in creating for PVA chatbot. The second file named 'Storing details" outlines steps needed to store the details from chatbot to shsrepoint list using power automate. The last file named 'idCardGeneraation.md' outlines the steps to design the power automate flow that generates ID card and send the ID card to the student over email.

TIME TO BRING THIS SOLUTION TO LIFE! 💃🏾 🕺🏾 - 👩🏾‍💻 👨🏾‍💻

