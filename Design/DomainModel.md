# Cheetah Sign Domain Model

This is a diagram and description that represents the Cheetah Sign system.

## Diagram

```mermaid
classDiagram
    direction RL

    class Administrator {
        -uid: int
        -firstName: String
        -lastName: String
        -email: String
        -allDocuments: List[allDocumentsList]

        +uploadDocument() void
        +removeDocument(docId: int) void
        +storeAllDocuments(docId: int) void
        +getAllDocuments() allDocumentsList

    }

    class DocumentAction {
        -docId: int
        -uid: int
        -action: String
        -actionDate: datetime

        +signDocument(docId: int) void
        +sendDocument(docId: int) void
        +returnDocument(docId: int) void
        +auditTrail(action: String, docId: int, uid: int) void

    }

    class AuditTrail {
        -auditList: List[auditHistory]
        -auditAction: AuditType
        -uid: int
        -timestamp: datetime

        +createAudit(auditAction: String, uid: int)
        +viewAudits(docId: int) auditList
    }

    class DocumentManagement {
        -docId: int
        -docName: String

        -favoriteDocuments: List[favoriteDocumentsList]
        -readyDocuments: List[readyDocumentsList]
        -sentDocuments: List[sentDocumentsList]

        +prepareDocument(docId: int) void
        +saveDocumentToFavorites(docId: int) void
        +removeDocumentFromFavorites(docId: int) void

        +addReadyDocuments(docId: int) void
        +addSentDocuments(docId: int) void
        +viewFavoriteDocuments() favoriteDocuments
        +viewReadyDocuments() readyDocuments
        +viewSentDocuments() sentDocuments
    }

    class Document {
        -docId: int
        -docName: String
        -status: DocumentStatus

        +getDocumentId() int
        +getDocumentName() String
        +getDocumentStatus() documentStatus
        +setDocumentId(docId: int)
        +setDocumentName(docName: String)
        +setDocumentStatus(status: DocumentStatus)
        +generateLink(docId: int) String

    }

    class Client {
        -uid: int
        -clientId: int
        -clientName: String
        -clientEmail: String
        -clientAddress: String
        -clientPhone: int
        -clientList: List[clients]

        +addClientToList(clientId: int) void
        +removeClientFromList(clientId: int) void
    }

    class DocumentStatus {
        <<Enumeration>>
        READY
        SENT
        IN_PROGRESS
        COMPLETED

    }

    class AuditType {
        <<Enumeration>>
        VIEWED
        SIGNED
        SENT
        COMPLETED

    }

    class SigningArea {
        -areaCoordinates: double
        -areaWidth: int
        -areaHeight: int

        +getCoordinates() double
        +getWidth() int
        +getHeight() int

        +setCoordinates(areaCoordinates: double)
        +setWidth(width: int)
        +setHeight(height: int)


    }


    Document "1"--*"*" DocumentAction
    Document "*"--*"1" DocumentManagement
    DocumentManagement "1"--"*" SigningArea
    Administrator "1"--"*" Document
    DocumentAction "1"--"1" AuditTrail
    DocumentAction ..> DocumentStatus
    AuditTrail ..> AuditType
    Client "*"--"1" Administrator

```

## Classes

### Administrator

The Administrator class represents the main users of the system. This is where the documents will first be uploaded by the admin. We want to provide a login feature so each admin has their own documents and customization. All documents, actions, and audit trails are saved to each admin user.

### Document

The document class represents the place where all documents will start. This is where you the document's id, name, and status will be set. Document has a parent-child relationship with the DocumentManagement and DocumentAction classes.

### DocumentAction

The DocumentAction class contains everything you need to use your documents. You can sign, send, and return documents here. Also, this is where you audit trail will be logged depending on the action you perform. The DocumentAction class holds a relationship with the AuditTrail class to log audits.

### DocumentManagement

This is where you will be managing your documents in various ways. In our system, we want to be able to sort documents depending on their status. For example, documents that are ready for sending and documents that have been sent. Furthermore, we want to offer some customization for the Administrator by letting them favorite frequently used documents.

### AuditTrail

The AuditTrail class is responsible for logging all actions performed on documents to form an audit trail. It will keep track of audit type, the user who made the audit, and the time it happened.

### SigningArea

The SigningArea class is the last piece of the document management. This class will be used to specify exactly where the designees need to sign by marking coordinates of the page.

### Client

The Client class will be used by administrators to save their client's information.

### AuditType

This class is an enumeration that defines the various audit types whenever an action on a document takes place. This well help keep a trail of all document audits. The possible audit types include:
<br>
**SENT**: Indicates that the document has been sent to the designees.
<br>
**VIEWED**: Indicates that the designee has opened the document.
<br>
**SIGNED**: Indicates that the designee has signed the document
<br>
**COMPLETED**: Indicates that all actions related to the document are finished and it is fully processed.

Some audit types might be modified or added in the future depending on our requirements.

### DocumentStatus

This class is an enumeration that defines the various statuses that a document can have throughout its lifecycle. Each status represents a specific state of the document, allowing for tracking each step it is on. The possible statuses include:
<br>
**READY**: Indicates that the document has been finalized and is ready for sending/signing.
<br>
**SENT**: Indicates that the document has been sent to the designees.
<br>
**IN_PROGRESS**: Indicates that the document has been opened by the designee.
<br>
**COMPLETED**: Indicates that all actions related to the document are finished and it is fully processed.

Some statuses might be modified or added in the future depending on our requirements.
