Session hijacking/replay, forgery, and injection attacks are difficult to identify, but the starting points for detection are likely to be URL analysis and the web server's access log.

### Uniform Resource Locator Analysis

As well as pointing to the host or service location on the Internet (by domain name or IP address), a Uniform Resource Locator (URL) can encode some action or data to submit to the server host. This is a common vector for malicious activity.

![An illustration represents URL analysis.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/1155-1692974875933.png)Description

http colon slash slash trusted dot foo slash is the URL for a trusted domain with a vulnerable script.  upload dot php question mark post equal to is the query.

percent 3Cscript percent 3D percent 27http percent 3A percent 2F percent 2F is the percent encoding.  zyxcba dot foo percent 2Frat percent 2Ejs percent 27 percent 3E percent 3C slash script percent 3E is the obfuscated domain hosting malicious script.

Uniform Resource Locator (URL) analysis.

As part of URL analysis, it is important to understand how HTTP operates. An HTTP session starts with a client (a user-agent, such as a web browser) making a request to an HTTP server. The connection establishes a TCP connection. This TCP connection can be used for multiple requests, or a client can start new TCP connections for different requests. A request typically comprises a method, a resource (such as a URL path), version number, headers, and body. The principal methods are the following:

- **GET** —retrieve a resource.
- **POST** —send data to the server for processing by the requested resource.
- **PUT** —create or replace the resource.

Data can be submitted to a server either by using a POST or PUT method and the HTTP headers and body, or by encoding the data within the URL used to access the resource. Data submitted via a URL is delimited by the ? character, which follows the resource path. Query parameters are usually formatted as one or more name=value pairs, with ampersands delimiting each pair.

The server response comprises the version number and a status code and message, plus optional headers, and message body. An HTTP response code is the header value returned by a server when a client requests a URL, such as 200 for "OK" or 404 for "Not Found."

### Percent Encoding

A URL can contain only unreserved and reserved characters from the standard set. Reserved characters are used as delimiters within the URL syntax and should only be used unencoded for those purposes. The reserved characters are the following:

: / ? # [ ] @ ! $ & ' ( ) * + , ; =

There are also unsafe characters, which cannot be used in a URL. Control characters, such as null string termination, carriage return, line feed, end of file, and tab, are unsafe. Percent encoding allows a user-agent to submit any safe or unsafe character (or binary data) to the server within the URL. Its legitimate uses are to encode reserved characters within the URL when they are not part of the URL syntax and to submit Unicode characters. Percent encoding can be misused to obfuscate the nature of a URL (encoding unreserved characters) and submit malicious input.