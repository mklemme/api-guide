# APIs
## Resources
- Download the chrome extension: [postman](https://www.getpostman.com/). It's an easy way to make api requests with a point-and-click interface
- Use http://jsonplaceholder.typicode.com/ to try out interacting with a restful api
- Check out this [list](https://github.com/toddmotto/public-apis) to get started with some apis
## Terms

| Term | Definition |
|--|--|
| `REST` | Representational state transfer |
| `API` | Application Programming Interface |
| `HTTP` | hypertext transfer protocol |
| `JSON` | Javascript Object Notation |
| `cURL` | Client URL |
| `auth key` | A unique token used to access private apis |

## Overview

### What is an API?

An API is a way to interact and fetch information from a third-party server.
- Google maps let's you display a map using their service
- Facebook has an api to access a user's profile information

### How it works
![pastedimage0](https://user-images.githubusercontent.com/1305776/43059588-f1c4a8d6-8e01-11e8-9dd1-51a658f9aa2d.png)

### RESTful apis

APIs that follow the restful architecture use certain HTTP methods

| Operation | SQL | HTTP |
|--|--|--|
| Create | `INSERT` | `PUT`/`POST` |
| Read | `SELECT` | `GET` |
| Update | `UPDATE` | `PUT`/`PATCH` |
| Delete | `DELETE` | `DELETE` |

### Query params

Query params are a key-value based way of including data in the url:

`https://example.com/resource-name?param1=value1&param2=value2`

### Response codes

A server will send a response code to represent whether or not the request was successful. 

| Range | Type |
|--|--|
| 1xx | Informational | 
| 2xx | Successful response. This might be sent after fetching a list of posts or creating a new comment. | 
| 3xx | Redirect or other non-critical response | 
| 4xx | Something happened from a user error. (Bad data or invalid url) | 
| 5xx | Something happened and the server broke. (Internal server error) | 

The most common response codes are:
- 200: OK
- 201: Created
- 302: Redirected permanently
- 401: Unauthorized
- 403: Forbidden
- 404: Not found

View all the response codes here: https://www.restapitutorial.com/httpstatuscodes.html

## Examples
### Browser/URL 
Query parameters are a quick way to filter items, sort or other actions like pagination.

*A json response for a collection of items*  

<img width="701" alt="screen shot 2018-07-22 at 8 04 58 pm" src="https://user-images.githubusercontent.com/1305776/43055286-b218b1f8-8dea-11e8-855f-801705ea106a.png">

*A json response for just user 2's posts*  

<img width="704" alt="screen shot 2018-07-22 at 8 04 35 pm" src="https://user-images.githubusercontent.com/1305776/43055285-b1fd3266-8dea-11e8-8d14-7662f190c68d.png">

### Curl
```bash
$ curl https://jsonplaceholder.typicode.com/posts/1

{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
```

If you would like to view the `response` headers, just include the `-i` flag:

```bash
$ curl -i https://jsonplaceholder.typicode.com/posts/1

HTTP/1.1 200 OK
Date: Mon, 23 Jul 2018 02:46:52 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 292
Connection: keep-alive
Set-Cookie: __cfduid=d567237e2d5d23379bc7545bf374af7ff1532314012; expires=Tue, 23-Jul-19 02:46:52 GMT; path=/; domain=.typicode.com; HttpOnly
X-Powered-By: Express
Vary: Origin, Accept-Encoding
Access-Control-Allow-Credentials: true
Cache-Control: public, max-age=14400
Pragma: no-cache
Expires: Mon, 23 Jul 2018 06:46:52 GMT
X-Content-Type-Options: nosniff
Etag: W/"124-yiKdLzqO5gfBrJFrcdJ8Yq0LGnU"
Via: 1.1 vegur
CF-Cache-Status: HIT
Expect-CT: max-age=604800, report-uri="https://report-uri.cloudflare.com/cdn-cgi/beacon/expect-ct"
Server: cloudflare
CF-RAY: 43ead1af58f56dc0-SJC

{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
```
### Postman
<img width="901" alt="screen shot 2018-07-22 at 10 32 52 pm" src="https://user-images.githubusercontent.com/1305776/43059793-06aefd90-8e03-11e8-8513-8dc907d5b8ef.png">

### jQuery
You can test this the [demo api](http://jsonplaceholder.typicode.com/) site directly:
- Open your developer console (`CMD+OPT+i`)
- Paste this in the console and run it (`ENTER`)
```javascript
var url = "http://jsonplaceholder.typicode.com/posts/1";

$.get(url,
  function(response) {
    console.log(response);
  }
);

{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
```
#### Private API
```javascript
var url = "https://api.giphy.com/v1/gifs/search?q=dog&api_key=zSGpBv8GUGZciSVedQztiYQlVs6n4Mzg";
// `?q=dog` represents the query param with value of 'dog'
// &api_key=zSGpBv8GUGZciSVedQztiYQlVs6n4Mzg is the unique key to access the api

$.get(url,
  function(response) {
    console.log(response);
  }
);

{
  data: [
    {
      type: "gif", 
      id: "mCRJDo24UvJMA", 
      slug: "dog-shiba-inu-typing-mCRJDo24UvJMA", 
      url: "https://giphy.com/gifs/dog-shiba-inu-typing-mCRJDo24UvJMA", 
      bitly_gif_url: "https://gph.is/1gSRt8W"
    },
    {
      type: "gif", 
      id: "dTJd5ygpxkzWo", 
      slug: "dog-nirvana-doggie-dTJd5ygpxkzWo", 
      url: "https://giphy.com/gifs/dog-nirvana-doggie-dTJd5ygpxkzWo", 
      bitly_gif_url: "https://gph.is/2cdgtLv"
    }
  ],
  pagination: {
    total_count: 135723, 
    count: 25, 
    offset: 0
  },
  meta: {
    status: 200, 
    msg: "OK", 
    response_id: "5b5648554f44336b558c5ba2"
  }
}
```
### Ruby
```ruby
require 'net/http'
require 'json'

url = URI.parse('https://jsonplaceholder.typicode.com/posts/1')
http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true # some apis only support https
request = Net::HTTP::Get.new(url.request_uri)
response = http.request(request)

p JSON.parse(response.body)

=> {
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}

```

