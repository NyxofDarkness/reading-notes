# Readings: SENDING FORM DATA

## Sending Form Data

what happens when a user submits a form?

1. where does the data go
> An HTML form on a web page is nothing more than a convenient user-friendly way to configure an HTTP request to send data to a server. This enables the user to provide information to be delivered in the HTTP request.

> The <form> element defines how the data will be sent
>  two most important attributes are action and method
> The action attribute defines where the data gets sent
> In this example, the data is sent to an absolute URL — https://example.com:
```
<form action="https://example.com">
Here, we use a relative URL — the data is sent to a different URL on the same origin:

<form action="/somewhere_else">
When specified with no attributes, as below, the <form> data is sent to the same page that the form is present on:

<form>
```
>VERY IMPORTANT: It's possible to specify a URL that uses the HTTPS (secure HTTP) protocol. When you do this, the data is encrypted along with the rest of the request, even if the form itself is hosted on an insecure page accessed using HTTP. On the other hand, if the form is hosted on a secure page but you specify an insecure HTTP URL with the action attribute, all browsers display a security warning to the user each time they try to send data because the data will not be encrypted.

> ames and values of the non-file form controls are sent to the server as name=value pairs joined with ampersands
>  action value should be a file on the server that can handle the incoming data, including ensuring server-side validation. The server then responds, generally handling the data and loading the URL defined by the action attribute, causing a new page load (or a refresh of the existing page, if the action points to the same page
> method attribute defines how data is sent.
> he GET method is the method used by the browser to ask the server to send back a given resource: "Hey server, I want to get this resource."
```
> The HTTP request looks like this:

GET /?say=Hi&to=Mom HTTP/2.0
Host: foo.com
```

> HTTP requests are never displayed to the user (if you want to see them, you need to use tools
> Open the developer tools.
1. Select "Network"
2. Select "All"
3. Select "foo.com" in the "Name" tab
4. Select "Headers"


2. how do we handle it when it gets there

> PHP offers some global objects to access the data


## Additional Resources
## HTML5 Forms Reference
> Pay special attention to the “action” and “method” attributes.

> php-example.html file — which contains the same example form as we saw before, with a method of POST and an action of php-example.php. When it is submitted, it sends the form data to php-example.php, which contains the PHP code seen in the above block. When this code is executed, the output in the browser is Hi Mom.

>  locally — browsers cannnot interpret PHP code, so when the form is submitted the browser will just offer to download the PHP file for you. To get it to work, you need to run the example through a PHP server of some kind

> Sending files with HTML forms is a special case. Files are binary data — or considered as such — whereas all other data is text data. Because HTTP is a text protocol, there are special requirements for handling binary data.

> If you want to send files, you need to take three extra steps:

1. Set the method attribute to POST because file content can't be put inside URL parameters.
2. Set the value of enctype to multipart/form-data because the data will be split into multiple parts, one for each file plus one for the text data included in the form body (if text is also entered into the form).
3. Include one or more <input type="file"> controls to allow your users to select the file(s) that will be uploaded.

> Each time you send data to a server, you need to consider security. HTML forms are by far the most common server attack vectors (places where attacks can occur). The problems never come from the HTML forms themselves — they come from how the server handles data

> All data that comes to your server must be checked and sanitized. Always. No exception.

1. Escape potentially dangerous characters. The specific characters you should be cautious with vary depending on the context in which the data is used and the server platform you employ, but all server-side languages have functions for this. 
2. Things to watch out for are character sequences that look like executable code (such as JavaScript or SQL commands).
3. Limit the incoming amount of data to allow only what's necessary.
4. Sandbox uploaded files. Store them on a different server and allow access to the file only through a different subdomain or even better through a completely different domain.

## Video Series on Styling HTML5 Forms: Looked over and bookmarked for further education!
