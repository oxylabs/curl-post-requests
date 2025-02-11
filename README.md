[![Oxylabs promo code](https://raw.githubusercontent.com/oxylabs/product-integrations/refs/heads/master/Affiliate-Universal-1090x275.png)](https://oxylabs.go2cloud.org/aff_c?offer_id=7&aff_id=877&url_id=112)

# How to Send Post Requests With cURL

- [How to Send Post Requests With cURL](#how-to-send-post-requests-with-curl)
  * [Sending POST requests](#sending-post-requests)
  * [Specifying the Content-Type](#specifying-the-content-type)
  * [Posting JSON](#posting-json)
  * [Posting XML](#posting-xml)
  * [Sending a file or multiple files via POST](#sending-a-file-or-multiple-files-via-post)
  * [Sending authentication credentials](#sending-authentication-credentials)

cURL is a powerful command-line tool for transferring data over various network protocols, including HTTP, HTTPS, FTP, and more. Since POST is a request method of HTTP & HTTPS protocols, cURL makes sending POST requests a one-line command that you can [run in your terminal](https://oxylabs.io/resources/integrations/terminal) easily. 

Find the [full article](https://oxylabs.io/blog/curl-post-requests) on our website.

## Sending POST requests

First, install cURL if you haven’t installed it already. You can find the installation instructions in our [How to Use cURL With Proxy](https://oxylabs.io/blog/curl-with-proxy) blog post.

The basic syntax for sending a POST request using cURL is as below:

```
curl -X POST -d "Hello" https://example.com/api
```

Notice the ```-X``` flag followed by ```POST```, it tells cURL to make a request using the HTTP protocol’s POST method, and the ```-d``` flag sets request data as ```Hello``` and sends it to the website https://example.com/api. The ```-X``` flag is the short form of the command line option ```--request```. 

## Specifying the Content-Type

Like any HTTP request, POST requests created using cURL can also have custom headers. For specifying the ```Content-Type``` header, you’ll have to set it using the header flag. 

```
curl -X POST -H "Content-Type: text/plain" -d "Hello" https://example.com/api
```

In the above command, there’s an additional ```-H``` flag which lets users [send custom HTTP request headers via cURL](https://oxylabs.io/blog/curl-send-headers). In this case, by specifying the ```Content-Type``` header as ```text/plain``` you’re letting the web server know that the request body data is in TEXT format. 

## Posting JSON

It’s also possible to send JSON data in the request body. All you need to do is set the appropriate ```Content-Type``` header and pass the JSON data with the ```-d``` flag. cURL will make a POST request with the JSON data specified in the argument.

```
curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' https://example.com/api
```

If you need a straightforward way to create a JSON code from a cURL command, use this [cURL to JSON converter](https://oxylabs.io/tools/curl-converter/json).

## Posting XML

Similar to JSON, you can also send XML in the request body. You’ll have to make changes to the request header and set it to ```application/xml```.

```
curl -X POST -H "Content-Type: application/xml" -d '<?xml version="1.0" encoding="UTF-8"?><root><name>John Doe</name><age>30</age></root>' https://example.com/api
```

## Sending a file or multiple files via POST

To send a file via cURL POST, you’ll have to use the ```-F``` flag. Pay attention to the capitalization of the letter “F”. All of the cURL flags or command line options are case-sensitive.

```
curl -X POST -F "file=@/path/to/img.png" https://example.com/api/upload
```

As you can see, the above command is uploading an image file. Right after the ```-F``` the file path of the image was given. You can also use multiple ```-F``` flags to send multiple files to the server as below:

```
curl -X POST -F "file=@/path/to/img1.png" -F "file=@/path/to/img2.png" https://example.com/api/upload
```

## Sending authentication credentials

You can use the ```-u``` flag or the ```--user``` option to specify the username & password for basic authentication. cURL will automatically create the Authorization header based on your input. 

```
curl -u username:password https://example.com/login
```

You’ll have to replace ```username``` and ```password``` with the actual authentication credentials. Also, don’t forget to replace the example URL with your own.
