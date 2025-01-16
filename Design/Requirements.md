# Requirements

## Functional Requirements

### Use Case 1

- FR1 - The system will be able to handle uploads and store documents in both .pdf and .docx formats.

  - UC1
  - High Priority

- FR19 - The system will be able to render .pdf and .docx formats for viewing.

  - UC1
  - High Priority

- FR2 - The system will be able to organize the stored documents held within it (FR1) by alphabetic order or in chronological order of creation, or a reverse of either.
  - UC1
  - Medium Priority
- FR3 - The system will have a separated list of 'favorited' documents, chosen dynamically by the administrators, that is a subset of the stored documents (FR1).
  - UC1
  - Medium Priority
- FR4 - The system will have a separated list of 'sent for signing' documents, added by the system with every document that is sent from the administrator to an outside party to be signed, that is a subset of the stored documents (FR1).
  - UC1
  - Medium Priority
- FR5 - The system will have a separated list of 'returned' documents, added by the system with every document that is sent from an outside party to the administrator after it has been signed, that is a subset of the stored documents (FR2).

  - UC1
  - Medium Priority

- FR14 - The system will allow for deletion of stored documents (FR1).
  - UC1
  - High Priority

### Use Case 2

- FR6 - The system will allow outside parties to click on the areas previously specified by the administrators (FR11) within the document and input the required information (signing).
  - UC2
  - High Priority
- FR7 - The system will provide a UI-based button that will state 'save changes' that appears upon any change to the document, including but not limited to creation and filling of text fields within the document. Upon clicking the button, the document will save all data held within and replace the original document.
  - UC2
  - High Priority
- FR8 - The system will provide a UI-based button that will state 'clear' that appears upon filling of any of the given text fields. Upon clicking the button, the document will empty the contents of all populated text fields.
  - UC2
  - Medium Priority
- FR9 - The system will work as a standalone program that houses all documents related to each individual user, or group of users, and is able to send these documents to other users via email. This document will be sent as a browser link.
  - UC2
  - High Priority
- FR10 - Upon receiving an email with a document to be filled and returned, the outside party will be able to edit the document within the website associated within the link provided. This editing will be limited to filling out the text fields, not changing any other contents of the document.
  - UC2
  - High Priority

### Use Case 3

- FR11 - The system will allow administrators to alter a document by specifying where information is needed. This information will include, but will not be limited to: full legal name and date of signature. Once all text fields are placed and specified, refer to FR1.
  - UC3
  - High Priority
- FR12 - The system will retain the location and the specification of all text fields placed by the administrator through all subsequent openings and editing of the document.

  - UC3
  - High Priority

- FR20 - The system should be able to generate a link to an altered document for signing
  - UC3
  - High Priority

### Use Case 4

- FR13 - The system will provide users a UI-based button labeled 'Return' to outside parties editing the document they were sent if and only if they have filled each required text field. This button will prompt a confirmation of the user, and upon confirmation will reply to the email with confirmation that the document has been signed.
  - UC4
  - High Priority
- FR15 - When the 'Return' button (FR13) is clicked, the system will save and a copy of the document will be sent back to the administrator that had originally sent the document for signing, replacing the version of the document found within the system under 'sent for signing' documents (FR4) but instead put into 'received' documents (FR5). This does not replace the original, unsigned document.
  - UC4
  - High Priority

### Use Case 5

- FR16 - The system will store an audit trail within the data of each document separately. This audit trail will include, but may not be limited to: time and date of upload to the system (FR1), time and date of any edits to the text fields within a document (FR11), time and date of when the document was sent to an outside party for signing (FR9), time and date of when the document was signed (FR10) and/or returned (FR13)

  - UC5
  - High Priority

- FR17 - The system will have separate administrative tools for checking the audit trail of each document (FR16) and will not be visible to outside parties beyond a confirmation of time and date of when they have received the document to be signed (FR9) and time and date of when they signed (FR10) and/or returned the document (FR13)
  - UC5
  - High Priority

### Use Case 6

- FR18 - The system will require a valid and consistent username and password in a login system from administrators in order to allow them to access the confidential information stored by the system (FR1).
  - UC6
  - High Priority

## Non-functional Requirements

- NR1 - The audit trail (FR 16) will not be visible directly within the document, but rather in the administrative tools found elsewhere in the system (FR17)
  - UC5
  - High Priority
- NR2 - Documents can populate multiple lists, as there is the original version of the document and the signed version that are stored separately (FR15)

  - UC1
  - Low Priority

- NR3 - When a file is sent over email (FR9), the administrators will be able to send a full email that also includes the link, it will not be an otherwise empty email that only houses the link.
  - UC2
  - Low Priority
- NR4 - When the program opens, the login screen (FR19) will be the first page visible to the administrators
  - UC6
  - Medium Priority
