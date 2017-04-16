# HTTP

## Routing
### Simpler Route
```ruby
#src/routes/web.cr

get "/" do
  "Hello World!"
end
```
All Routes are declared on the file ```src/routes/web.cr```

when you visit ```http://localhost/```
you will see the page return "Hello World!"


This endpoint retrieves all kittens.

## REST Calls
```ruby
#src/routes/web.cr

get "/" do
.. show something ..
end

post "/" do
.. create something ..
end

put "/" do
.. replace something ..
end

patch "/" do
.. modify something ..
end

delete "/" do
.. annihilate something ..
end
```

You can handle HTTP methods as easy as writing method names and the route with a code block. Kemal will handle all the hard work.

## Static Files

```html
#Files

app/
  src/
    your_app.cr
  public/
    js/
      jquery.js
      your_app.js
    css/
      your_app.css
    index.html
```

 > Open index.html and add

```html
#src/public/test.html

<html>
 <head>
   <script src="/js/jquery.js"></script>
   <script src="/js/your_app.js"></script>
   <link rel="stylesheet" href="/css/your_app.css"/>
 </head>
 <body>
   ...
 </body>
</html>
```

Add your files to public directory and Kemal will serve these files immediately.


##Static File Options
```ruby
#src/rocky.cr

serve_static false
```

###Disabling Static Files
By default Kemal serves static files from public folder. If you don’t need static file serving at all(if you are only running an API) you can disable it



##Error Handling
Error handlers run within the same context as routes and before filters which means you get all the power of those.

##404 Not Found
```ruby
error 404 do
  "This is a customized 404 page."
end

```
When a ```Kemal::Exceptions::NotFound``` exception is raised, or the response’s status code is 404, the error 404 handler is invoked:

You can customize the built-in error 404 handler.


##Custom error handlers for status codes
Just like error 404 handler you can install custom error handlers for different status codes.

error 403 do
  "Access Forbidden!"
end

get "/" do |env|
  env.response.status_code = 403
end
