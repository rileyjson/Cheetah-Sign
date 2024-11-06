# User Manual

## Admin

Admins are in control of most of the functionality for Cheetah Sign. You have access to the admin side of the website, where
you will be able to:
- Upload Documents
- View Uploaded Documents
- Send Documents to Clients
- View the Status of Sent Documents



### Upload Documents

In order to send a document to a client, you must first upload it. You can do this by using the upload form found at the
bottom of the admin page. Select the "Browse..." button to open up your local file browser, and select the .PDF file that
you would like to upload. Cheetah Sign has been designed and tested with .PDF files only, and it is best for to try
and stick to those files. 

![UploadForm](./images/uploadButton.png)  
![FileBrowse](./images/fileSelection.png)

After selecting your .PDF file, click the green upload button. The file should be uploaded to the server and can be used. After
uploading the file, it is a good idea to reload the page.

### View Uploaded Documents

All uploaded files can be found under the "Uploaded Documents" table found in the middle of the page. Each document is listed
with the following attributes from left to right:
- The Document Name
- A text box for the client name
- A view button
- A send button

![UploadedDocumentsTable](./images/uploadedDocumentsTable.PNG)

If you click on the "view" button, you will be sent to the server link for the PDF. You can simply view the file and return,
or you can download the file. 

### Send Documents to Clients

Looking at the table of uploaded documents, you are able to create a "Job". A "Job" is an instance of a document that contains
a client and a status determining the state of the document. You can create a Job by filling out the client name text box and
selecting the "Send" button. You should reload the page after making a job.

![SendButton](./images/sendButton.PNG)

You can create as many Jobs as you'd like from a single document by continuing to select the Send
button. This is helpful when sending a single document to several clients, such as an NDA to a new team of hires.

### View the status of sent documents

All sent Jobs can be found at the top of the page. It details the document name, the client, and the status of the job. If
a document has been signed by the client, it will be marked with the status "signed". Otherwise, it will be marked with the
status "sent". 

![SentDocumentsTable](./images/sentDocumentsTable.PNG)

Each job in the table also has its own view button, allowing for you to view the document, similar to the view button on the
list of uploaded documents.

## Client

As a client, you will have the ability to:
- View Documents sent to you
- Sign Documents

### View Documents sent to you



### Sign Documents