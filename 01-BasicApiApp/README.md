## Step 1: Set up an API 
Set up a basic endpoint with the Web API

## Objectives 
- Set the Web API's dependencies and add it into the app via MVC (since it's in the same package) 
- Set up a basic endpoint

1. Set up MVC! The Web API has been merged into MVC, so it's all one package. 

And add this dependency for MVC to project.json, 

```
"Microsoft.AspNetCore.Mvc": "1.0.0"
```

Add this method to the Startup class: 

```
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvcCore();
}
```

Add this line to the Configure method in Startup:

```
app.UseMvc();
```

1. Add meaningful web components - appsettings, web.config

1. Add a controller to serve the API requests called `ArticlesController` and add the following. 

```
[Route("/api/[controller]")]
public class ArticlesController
{
  [HttpGet]
  public string Get() => "Hello, from the controller!";
}
```

Run the app and you should be able to hit localhost:5000/api/articles. 

When you are finished with this step, [continue to adding entity framework](https://github.com/Wyntuition/aspnetcore-workshop-kit/tree/master/03-EntityFramework)


TODO:
-Config, env 
-any other infra here? 
var builder = new ConfigurationBuilder()
                .SetBasePath(env.ContentRootPath)
                .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                .AddEnvironmentVariables();
            Configuration = builder.Build();