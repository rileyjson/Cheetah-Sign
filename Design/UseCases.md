# Actors



# Use Cases

### UC1: Manage Documents

**Why**: Managing documents refers to the act of storing, organizing, and making easily accessible within the scope of the Cheetah
Sign system. This is a vital part of the project - without being able to manage documents, the process of
sending documents to be signed will be impossible or take significantly longer with much more complex steps. 
Managing documents is vital to the efficiency of Cheetah Sign and should be a mainstay of the system.

If this is not implemented, it is likely that use of the Cheetah Sign system will be slow and clunky, as well as lacking
the ability to store documents, resulting in a direct clash with BR1.

**Actors**:

**Flow**: When the user is accessing Cheetah Sign GUI, the user should be able to select from the following options:
- Upload a document
- Select Favorited Documents
- Select Sent Documents
- Select Returned Documents

When selecting an option on the GUI, the user should be able to carry out the stated action. The specific steps taken
will be described in the functional requirements.

### UC2: Sign Documents


**Why**: Signing documents is the primary function of Cheetah Sign. The goal is to make a software that allows for
digital documents to be signed by multiple parties to create a legally binding agreement. Therefore, the ability to
sign documents is vital to the use of Cheetah Sign. 

Not implementing the ability to sign documents directly clashes with BR1.

**Actors**:

**Flow**: An administrator user should be able to access any given unsigned document through document management. When a
document has been selected, the user will then be able to click on the areas where signatures need to be placed. In the
implementation of additional information, users will also be able to click on areas where personal information must be input
(phone numbers, address, etc.) Once all required information has been filled out, the user should be able to "finish", 
finalizing their signature. The signed document should then be sent to the next party in order. 

If the user is a client, the steps above still apply except for how the document is accessed. As a user, the document
will likely be accessed through a web browser link where the document will be accessed and filled out.

### UC3: Prepare and Send Documents to Clients**


**Why**: Preparing a document refers to selecting where on the document(s) clients must provide information / sign.
If this aspect is not implemented, clients will not be able to sign the documents, making it impossible to create a 
legally binding agreement. Therefore, the ability to prepare and send documents is vital to the use of Cheetah Sign.

Not implementing the ability to prepare and send documents directly clashes with BR1.

**Actors**:

**Flow**: A Cheetah Sign administrator should access a document via the document management feature. Once a document has
been accessed, the administrator should be able to select a location on the document for a insert box to be placed. The
user will decide what kind of information should be placed there. Once all information boxes have been placed, the document
can then be sent to the various parties that are required to sign it.

### UC4: Sign and Return Documents to Admin**


**Why**:

**Actors**:

**Flow**:

### UC5: Log Audit Trail of Document Use**


**Why**:

**Actors**:

**Flow**: