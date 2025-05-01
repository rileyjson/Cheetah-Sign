## Details about the program for future developers and users:

Currently, the email system is hooked up to send from an actual email address. Before making use of it, ensure you change
this to a proper email address. The code can do so can be found in Cheetah.Sign.Api/endpoint-services/EmailSending.cs.

As of the moment, the program does not send to multiple users. If wanting to get signatures from multiple users, admin
will have to send the document to one user at a time, downloading the document and then re-uploading it back to the service
again.

