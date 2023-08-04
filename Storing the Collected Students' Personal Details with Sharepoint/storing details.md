
# Collecting Student Responses And Updating Them On Sharepoint With PowerAutomate

CONGRATULATIONS ON SUCCESSFULLY BUILDING YOUR BOT! Now let's connect our bot to our SharePoint using Power Automate. 
 
We start off by adding a new node to our bot after the first condition block which is equal to true. Remember how to add a node? Just click on the '+' sign. This time we would pick 'Call an action' and then 'Create a flow'. Clicking 'Create a flow' would open Power Automate in a new window as shown below. 

![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/0c842e91-2668-4fd5-9de1-d14200fd55bf)

Notice that two actions have been automatically added to our Power Automate flow. 

In the first action, Power Automate is establishing a connection with our Power Virtual Agent bot. We need to add each question the bot would ask or we would need a response to as input. 

To add the questions as inputs, click on '+ Add an input', then 'Text'. Notice that when you do, a new input box is added. Repeat this step for all the questions and fill in the details correctly. 

-	Input: Use the same variable name you assigned to each question in the bot as the name of the input. For example, FullName for the question to identify which department in your organization the employee works with, Question1 for the first question, Question2 for the second question, Question3 for the third question, and Question4 for the fourth question. 

-	Please enter your input: Enter each question as input. Ensure you input the questions as arranged on SharePoint and in your Power Virtual Agent bot. 
 
 
![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/3a9d7e83-0ced-4612-8203-ec3481e8e77f)

