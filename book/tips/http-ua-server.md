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

There is no unique way to detect HTTP server side `User-Agent` detection, but there are patterns that can be automated easily. The easiest and quickest one is to use a command line HTTP client such as [curl](http://curl.haxx.se/) or [httpie](http://httpie.org/) and to make the request to the same resource with a different `User-Agent` string. For example, using httpie.

Requesting an imaginary Web site at `http://www.example.com/` with Safari iOS 7 `User-Agent` string:

    → http HEAD http://www.example.com/ 'User-Agent: Mozilla/5.0 (iPhone; CPU iPhone OS 7_0 like Mac OS X) AppleWebKit/537.51.1 (KHTML, like Gecko) Version/6.0 Mobile/11A465 Safari/9537.53'

We could get this response from the server:

    HTTP/1.1 301 Permanent Redirect
    Age: 0
    Date: Tue, 16 Sep 2014 00:05:29 GMT
    Location: http://m.magazineluiza.com.br

While when requesting with Firefox OS `User-Agent` string.

    → http HEAD http://www.example.com/ 'User-Agent: Mozilla/5.0 (Mobile; rv:32) Gecko/32 Firefox/32'

we could get this response from the server:

    HTTP/1.1 200 OK
    Age: 365
    Cache-Control: public, max-age=600, s-maxage=450
    Content-Encoding: gzip
    Content-Length: 45752
    Content-Type: text/html; charset=UTF-8
    Date: Tue, 16 Sep 2014 00:06:01 GMT

We can notice right away that iOS is being redirected to a mobile Web site `301` status and `Location:` header, while Firefox OS is receiving a `200` and content probably tailored for Desktop.

Sometimes we can detect the differences through the size of the content which has been sent to different user agents through the `Content-Length` HTTP header.


## How to fix it

This really depends on the way the client detection has been organized. It might be handled by a server code library (PHP, ASP, etc.), it might be coming from a database or sometimes from a configuration file of the server itself. You need to find the person who is in control of the server and discuss with this person the chosen strategies for the server detection. External User agent databases can be very practical but they describe only the past. Any new User agent will fail, if it doesn't fit in the common patterns of the database. It means you need to rely on a rapid release update system and continue to pay the fees for seeing the Web site working in the future with new devices.

As Web developers, you can easily put in place a list of simple tests to check if the client is receiving the expected HTTP response headers for the `User-Agent` strings sent to the server. This becomes

## Benefits

* The immediate benefits is to reach out more devices, so more market share. Very often the User agent detection fails for no good reasons. The Web site is perfectly working on the device.
* The second reason is indirect but by ensuring that your Web site is accessible to more devices, you will avoid to target too specifically the star-device of the moment and reduce your maintenance cost for the future when another device has taken the lead.

## References
Put here additional references to documentation.
