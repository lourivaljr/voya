Voya Framework
====

Voya Framework is an integrated full-stack Java framework for rapid web development.
It's a simple but powerful dispatch action with no configuration required (convention over configuration).


Get Started!
====

Use the VoyaServlet in the web.xml configuration file and you're good to go.
The url are mapped over conventions. 

<domain>/ExampleController/method?name=john&year=1...
This url maps to a controller class method.

```
class MyBean
{
  private String name;
  private Integer year;
  
  set's...
  get's...
}


class ExampleController
{
  private HttpServletRequest request;
  private HttpServletResponse response;

  public ExampleController()
  {
  }
  
  public ExampleController(HttpServletRequest r, HttpServletResponse res)
  {
    this.request = r;
    this.response = res;
  }


  public MyBean method(MyBean b)
  {
    ...
    request.setAttribute("myVar", "<h2>Any text or object can go here</h2>");
    return b;
  }
}

```

Once the controller is done, a view with the same name (method.vm) is searched in the /templates dir. Whatever you return from method gets to the view as "object" variable. Voya uses Apache Velocity as the template engine for the view. So, in method.vm you'll have:

```
<html>
  ...
  <body>
    <h1>Hello $object.name</h1>
    $myVar
  </body>
</html>
```

This is it! Any variables you pass to the request can also be accessed from the template.
