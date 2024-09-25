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

### UC3: Prepare and Send Documents to Clients


**Why**: Preparing a document refers to selecting where on the document(s) clients must provide information / sign.
If this aspect is not implemented, clients will not be able to sign the documents, making it impossible to create a 
legally binding agreement. Therefore, the ability to prepare and send documents is vital to the use of Cheetah Sign.

Not implementing the ability to prepare and send documents directly clashes with BR1.

**Actors**:

**Flow**: A Cheetah Sign administrator should access a document via the document management feature. Once a document has
been accessed, the administrator should be able to select a location on the document for a insert box to be placed. The
user will decide what kind of information should be placed there. Once all information boxes have been placed, the document
will be saved as a "prepared" document. The prepared document can then be sent to clients to be filled out and returned.

### UC4: Sign and Return Documents to Admin


**Why**: A document must be signable by all parties, not just Administrators of the Cheetah Sign software. As such, it is
important that clients are able to sign the document and then send the signed document back to the admin for safekeeping
and processing. If a document is not signable by clients, then the document cannot become a legally binding agreement,
directly clashing with BR1.

**Actors**:

**Flow**: Clients will access the document sent to them via their email in a web browser. They will select the individual
areas where their signature and personal information is required, and then fill in the fields with the required information.
Once the required information has been filled out, they wil finish the document, where it will then be sent to the next
party - likely the administrator, but not necessarily.

### UC5: Log Audit Trail of Document Use


**Why**: Legally binding documents have an intense focus on date and time. If the date and time of a legally binding 
document is incorrect, then there can be several issues stemming from inconsistencies regarding timing. Furthermore, it
is vital to keep track of where a document currently is and who it has yet to be signed by. If these are not implemented,
it will be a massive loss of efficiency with the efforts taken to gather this information. Furthermore, it could result
in legal issues, both of which clash with BR1.

**Actors**:

**Flow**: From the GUI, Cheetah Sign administrators will be able to access uploaded documents and view the following
information. 
- When the document was uploaded.
- When the document was prepared

The sent documents will contain an audit trail with the following information:

- When the document was sent to clients
- When the document was opened by the client
- When the document was signed and returned by the client.

### UC6: Login System for Cheetah Sign Administrators


**Why**: 

**Actors**:

**Flow**: