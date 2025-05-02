# Cheetah Sign Future

## Current Issues

- Sometimes when uploading documents, the database will reorder them and they will not appear in the order of upload
- Sometimes after sending documents, the database will reorder the jobs and they will not appear in the order they were sent

## Potential Issues

- When highlighting each input step on the PDF for signer, it's possible that it can highlight incorrect text if you have text in your PDF that is the same as your input step

## Possible Improvements

- Find a way to prevent the database from reordering its fields
- Make a PDF sendable to multiple people for signing, and specfiy only their corresponding text boxes to sign

## Details about the program for future developers and users:

Currently, the email system is hooked up to send from an actual email address. Before making use of it, ensure you change
this to a proper email address. The code can do so can be found in Cheetah.Sign.Api/endpoint-services/EmailSending.cs.

As of the moment, the program does not send to multiple users. If wanting to get signatures from multiple users, admin
will have to send the document to one user at a time, downloading the document and then re-uploading it back to the service
again.

