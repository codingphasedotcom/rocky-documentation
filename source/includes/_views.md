#Views

## Render a View

Views are server side rendered pages

```ruby
#src/routes/web.cr

get "/account" do
  render "src/views/hello.ecr"
end
```
| Macro     | Value1 | Detail |
| :------- | ----: | ----: |
| render | src/views/hello.ecr | you pass down the ecr view that you want to render on that route |

## Pass Variables to View
### On The Route
```ruby
#src/routes/web.cr

get "/user" do |env|
  name = "Joe"
  render "src/views/hello.ecr"
end
```
You declare the route route and inside the block you declare the variable.

### On The View
```html
#src/views/hello.ecr

<div>
  <%= name %>
<div>
```
Now inside the ecr file which is the view you want to render. You want to do an embedded tag with the name of the variable so it can show on your page.


##Layouts
Layouts are a great way to keep your code DRY (Dont Repeat Yourself)
For example lets say all your pages have the same header and footer throughout all the pages and all that changes is the content area do you go and copy the header and footer to every page No... we just make one main layout and then set content tag where you will show your view.

> On The Route

### On The Route
```ruby
#src/views/pages/user.ecr

get "/user" do
  name = "joe"
  render "src/views/pages/user.ecr", "src/views/layouts/main.ecr"
end
```

| Macro     | Value1 | value2 | Detail |
| :------- | ----: | ----: | ----: |
| render | src/views/hello.ecr | src/views/layouts/main.ecr | you pass down the ecr view that you want to render on that route and layout page |
|  | view location | layout location |  |


### On The View
> On The View

```html
#src/views/hello.ecr

<div class="content-area">
  Hey, here goes my html
</div>
```

Just put the code you want to show up for that view

> On The Layout

### On The Layout
```html
#src/views/layouts/main.ecr

<html>
<head>
  <title>My Kemal Application</title>
</head>
<body>
  <header>
    <ul class="menu">
      <li><a href="#">Home</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </header>
  <%= content %>
</body>
</html>
```


Use ```<%= content %>``` tag to display the page content on the layout

## content_for & yield_content
content_for is a great for situations where you might want to change something from the layout on every view. For example a page title or a css script.

> On The View

### On The View
```html
#src/views/pages/hello.ecr

<% content_for "title" do %>
<title>My Kemal Application</title>
<% end %>

<% content_for "css" do %>
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<% end %>

<div class="content-area">
  this will be the view content
</div>

<% content_for "javascript" do %>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
<% end %>
```

Use the ```content_for``` and give it a name. You can have multiple content_for macros on a view. For example one for the title, another for css, and another for javascript.

> On The Layout

### On The Layout
```html
#src/views/layouts/main.ecr

<html>
<head>
  <%= yield_content "title" %>
  <%= yield_content "css" %>
</head>
<body>
  <header>
    <ul class="menu">
      <li><a href="#">Home</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </header>
  <%= content %>
  <%= yield_content "javascript" %>
</body>
</html>
```

add the ```yield_content``` with the name of the content you want to display.

## First View
```html
#src/views/includes/navigation.ecr

<ul class="menu">
  <li><a href="#">Home</a></li>
  <li><a href="#">Contact</a></li>
</ul>

```
You can include any view in another view


```html
#src/views/layouts/main.ecr

<html>
  <head>
    <%= yield_content "title" %>
    <%= yield_content "css" %>
  </head>
  <body>
    <header>
      <ul class="menu">
        <li><a href="#">Home</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </header>
    <%= render "src/views/includes/navigation.ecr" %>
    <%= content %>
    <%= yield_content "javascript" %>
  </body>
</html>

```
