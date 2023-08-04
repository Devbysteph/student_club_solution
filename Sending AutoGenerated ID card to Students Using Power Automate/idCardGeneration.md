# Overview

After getting the picture of the student, we need to use that picture to generate an ID card for the student. The convention to be used here is that the file name of the picture uploaded by the student should be exactly equal to the matriculation number of the student.  

# Solution 

Head over to powerautomate.microsoft.com and follow the following steps - 

- We would be using the trigger “When a file is created” in the OneDrive connector. The trigger asks for the location of the folder in the OneDrive where the file is to be uploaded. In our case, the file gets uploaded in the folder StudentSolutions/Pictures. To select the folder, click on the ‘Show Picker’ icon on the right side of the field and choose the folder needed.

  ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/1c62e149-8ce1-4d1b-9b20-eecc1c2b648a)<br>



- The next step is to get the file name of the picture that is uploaded. We would be initializing 2 variables to get the matriculation number from the file name  

  - fname – stores the file name of the picture that is uploaded. It contains extension as 	well. It is a string variable. 
    For examplee, fname contains ‘20637.jpg’. 
  
  - matNum -   This variable stores the actual matriculation number of the student. 	M	atriculation number is extracted from the filename by removing the extension from 	fname. This is done by using the expression

          <strong>substring(variables(‘fname’),0,lastindexof(variables(‘fname’),’.’))</strong> 
    In our case, matNum contains ‘20637’

    ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/9b897d0d-48bb-4670-bff8-4bf74a84f693)<br>

- Now, there are 2 cases- if the student uploads his/her picture using the link provided, without being signed in to the onedrive account, then, he/she would be asked the first name and the last name. the uploaded file is saved in the onedrive folder in the format <FirstName>_<LastName>_<FileName> where FileName is the actual name of the file. In order to get correct filename (which is equal to the matriculation number), following actions are used –
  
    i.	Check if the filename contains ‘_’ symbol or not. 

    ii.	If it contains, the actual file name is obtained by removing all the characters before the last ‘_’ symbol.         The updated filename is stored back in the variable matNum. 

    iii.	If no underscore (‘_’) symbol is present, then no changes are required. 

    ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/95efab23-36cb-476d-80e3-65e6dc0c1930)<br>

- In the next step, we are fetching the details for all the students from the SharePoint and comparing matriculation number of each record with the matNum variable. Since matriculation number of a student in an institution is always unique, therefore, we can safely conclude that the below flock of action returns only one record. The steps 5 to 10 generate the ID card for the student whose matriculation number matches with the filename of the picture provided and sends the generated id card as pdf to that student via email.

    ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/9ec468a6-ae17-4ed9-9f3e-1567085d2693)<br>

- For record matching with the filename, we perform the following steps in sequential order to generate and send the id card over email –

    ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/7ff5764e-39c4-4d31-8f4e-280c92269c9f)<br>

    <strong>i.	 Populate a Microsoft Word template </strong>

    Microsoft word template is the word document with image and text placeholders which give the layout of the ID card to be generated. 
  

  To populate a word document, we need Word (Online) connector. Search 	for the connector and select the action “Populate a Word Document”. 

  The Action requires 3 mandatory questions – 

  1.	Location – The location where the word template is stored (OneDrive for Business in our case) 

  2.	Document Library – OneDrive 

  3.	File – Browse and select the Microsoft Word template we created earlier. 

  After selecting the file, 2 new fields will be populated – the image and text 	control we added. For the image, we need to select the image that should 	be put in there. For this purpose, we can use the dynamic content from the 	“When a file is Created” trigger and select “File Content”.

  For the text control, we need to provide the name of the student. The name 	of the student is taken from the matching record of the “Get Items” action 	of SharePoint. So, the name is added dynamically.

  ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/961ad3ac-b19f-4bb7-ac4d-1c470e470ede)<br>


  ii.	Now, after we have provided the values for the image control and the text control, we need to create a new file to store the content of the id card. To do this, 

    - Create a new OneDrive Action “Create File” 

    - Provide the path to the folder where this file will be stored. 

    - Provide name of the file. Since this is just a temporary word document file, we will name it as “temp.docx”. [Note that this file will be deleted later after converting to pdf] 

    - For file content, add the dynamic content from the previous word template we created – “Microsoft Word Document”. 

    ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/c113fab2-cee6-464a-8db2-670ac347f406)<br>

 
  iii.	Add a new action called “Convert File” to convert our temporary file generated to pdf. The action takes values of 2 arguments as input – 
    
    1.	File – the unique identifier to the file which is to be converted. We will use dynamic content “id” of previous ‘Create file’ action. 

    2.	Target type – the target file type (pdf in our case).
 
    ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/09b250ac-c505-4c43-8b14-8387bb473acd)<br>

  iv.	Till now, we have created a word document of the ID card, converted the word document to pdf format. Now, its time to store the pdf in OneDrive. For this we will be using the action of OneDrive Connector called “Create File”. 

    - Like step ii, we need to provide the destination folder path, file name and file content. 

    - The file content will be dynamic content called “File Content” of the previous action (Convert file action).

    ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/346554e6-5dff-48bc-917c-9b867e181a8d)<br>


  <strong>v.	Sending email </strong>
      The last step is to send an email to the student with the ID card added to it 	as attachment. For this purpose, we are using “Send an email” action of onedrive. 

    - The target email address is obtained from the matching record we got using 	the ‘Get items’ action. 

    - In order to add the pdf file of the id card as attachement, use the dynamic content ‘Body’ of ‘Convert File’ action. 

  ![image](https://github.com/Devbysteph/student_club_solution/assets/74033507/a31dbd87-74c2-419b-8764-0fd276995597)<br>


  That's it. Pretty Cool. Isn't it

  CONGRATULATIONS for successfully building the solution from scratch!








