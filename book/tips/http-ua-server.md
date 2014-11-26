Title: HTTP User Agent Detection on the server side
Category: http
Created: 2014-11-26
Updated: 2014-11-26

## Description

HTTP is based on request/response protocol. The client (ex: browser) sends a HTTP request to the server. The server replies with a HTTP response. With each request, the client sends information under the forms of HTTP headers.

    Host: www.example.com
    User-Agent: Mozilla/5.0 (Mobile; rv:35.0) Gecko/35.0 Firefox/35.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    Accept-Encoding: gzip, deflate
    Connection: keep-alive
    Cache-Control: max-age=0

The HTTP header `User-Agent` identifies the client. It is very often used by servers to deliver content targetting this specific browser. For example, it is used for delivering content designed for Mobile devices instead of Desktop. It is also used for redirecting the browser to the mobile Web site.

Sometimes users will receive the wrong content or wrong expected user experience, very often the desktop content instead of the mobile content. Sometimes users will be completely denied the access to the Web site.

## How to detect
Explain what are the ways of investigating the issue. You may add a couple of images and code samples.

## How to fix it
What is the simplest way to fix it? If there is a process you can use to do it, explain it. If there are tools, give them.

## Benefits
Explain why it would be beneficial to fix it (apart of being a better Web citizen).

## References
Put here additional references to documentation.
