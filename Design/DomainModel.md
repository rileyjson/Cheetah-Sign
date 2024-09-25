# Cheetah Sign Domain Model

## Diagram

```mermaid
classDiagram
    direction RL
    class Document {
        -docId: int
        -docName: String
        -status: documentStatus

        +uploadDocument() void
        +getDocumentId() int
        +getDocumentName() String
        +getDocumentStatus() DocumentStatus
        +setDocumentId(docId)
        +setDocumentName(docName)
        +setDocumentStatus(status)

    }

    class Action {
        -docId: int
        -docName: String
        -status: documentStatus
        -uid: int
        +auditType: String
        +uid: int

        +defineSigningAreas()
        +sendDocument()
        +storeDocument()
        +removeDocument()
        +getDocuments() List[Documents]
        +auditTrail(auditType, uid)
    }

    class Administrator {
        -uid: int
        -name: String
        -email: String
        -frequentDocuments: List[documentStorage]

        addDocumentToList()
        removeDocumentFromList()
        viewDocumentList() List[documentStorage]
    }

    class Client {
        -uid: int
        -clientId: int
        -clientName: String
        -clientEmail: String
        -clientAddress: String
        -clientPhone: int
        -clientList: List[clients]

        addClientToList()
        removeClientFromList()
    }

    class DocumentManagement {
        -storedDocuments: List[documentStorage]

        addDocumentToList()
        removeDocumentFromList()
        viewDocumentList()

    }

    class DocumentStatus {
        <<Enumeration>>
        SENT
        WAITING
        COMPLETED

    }

    class AuditTrail {
        +auditType: String
        +uid: int
        +timestamp: datetime

        createAudit()
        viewAudits()
    }

    Administrator -- "*" Client
    Document --o AuditTrail
    Document --> DocumentStatus
    Administrator "1"o--"*" Document
    Document -- Action
    Administrator --o DocumentManagement
    Action --> AuditTrail

```

## Classes

### Document

The document class represents the documents that have been uploaded. You can get and set document ID, name, and status.

### Action

The Action class contains everything you will need to perform actions on the documents.

### DocumentManagement

This is where the document management operations will take place. Administrators will be able to utilize this class and their methods.

### AuditTrail

This class represents keeping track of all actions on documents to form an audit trail. It will keep track of audit type, the user who made the audit, and timestamps.

### Administrator

The Administrator class represents the main users of the system. They will be able to utilize the Document Management class. They can store, remove, and view their frequently used documents for easier access.

### Client
