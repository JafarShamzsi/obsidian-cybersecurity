Metadata is the properties of data as it is created by an application, stored on media, or transmitted over a network. Each logged event has metadata, but a number of other metadata sources are likely to be useful when investigating incidents. Metadata can establish timeline questions, such as when and where a breach occurred, as well as containing other types of evidence.

### File

File metadata is stored as attributes. The file system tracks when a file was created, accessed, and modified. A file might be assigned a security attribute, such as marking it as read-only or as a hidden or system file. The ACL attached to a file showing its permissions represents another type of attribute. Finally, the file may have extended attributes recording an author, copyright information, or tags for indexing/searching.

As metadata is uploaded to social media sites, they can reveal more information than the uploader intended. Metadata can include current location and time, which is added to media such as photos and videos.

### Web

When a client requests a resource from a web server, the server returns the resource plus headers setting or describing its properties. Also, the client can include headers in its request. One key use of headers is to transmit authorization information in the form of cookies. Headers describing the type of data returned (text or binary, for instance) can also be of interest. The contents of headers can be inspected using the standard tools built into web browsers. Header information may also be logged by a web server.

### Email

An email's Internet header contains address information for the recipient and sender, plus details of the servers handling transmission of the message between them. When an email is created, the mail user agent (MUA) creates an initial header and forwards the message to a mail delivery agent (MDA). The MDA should perform checks that the sender is authorized to issue messages from the domain. Assuming the email isn't being delivered locally at the same domain, the MDA adds or amends its own header and then transmits the message to a message transfer agent (MTA). The MTA routes the message to the recipient, with the message passing via one or more additional MTAs, such as SMTP servers operated by ISPs or mail security gateways. Each MTA adds information to the header.

Headers aren't exposed to the user by most email applications. You can view and copy headers from a mail client via a message properties/options/source command. MTAs can add a lot of information in each received header, such as the results of spam checking. If you use a plaintext editor to view the header, it can be difficult to identify where each part begins and ends. Fortunately, there are plenty of tools available to parse headers and display them in a more structured format. One example is the Message Analyzer tool, available as part of the Microsoft Remote Connectivity Analyzer ([testconnectivity.microsoft.com/tests/o365](https://testconnectivity.microsoft.com/tests/o365)). This will lay out the hops that the message took more clearly and break out the headers added by each MTA.

![A screenshot shows the analysis of a phishing message.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/7859-1692974873810.png) Description

The page lists the subject, correspondents, and date at the top in a tabular format and the message at the bottom. A dialogue box on the top analyze the source of the message.

_Analyzing headers in a phishing message: the sender is using typosquatting to hope the recipient confuses structurealty.com with the genuine domain_ _structureality.com__. (Screenshot courtesy of Mozilla.)_ (Screenshot courtesy of Mozilla.)