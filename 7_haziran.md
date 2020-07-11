# **RazorASP.NET Core**

Razor Pages can make coding page-focused scenarios easier and more productive than using controllers and views.

## Razor Pages

Razor Pages is enabled in _Startup.cs_:

publicclassStartup

{

publicStartup(IConfiguration configuration)

{

Configuration = configuration;

}

public IConfiguration Configuration { get; }

publicvoidConfigureServices(IServiceCollection services)

{

services.AddRazorPages();

}

publicvoidConfigure(IApplicationBuilder app, IWebHostEnvironment env)

{

if (env.IsDevelopment())

{

app.UseDeveloperExceptionPage();

}

else

{

app.UseExceptionHandler(&quot;/Error&quot;);

app.UseHsts();

}

app.UseHttpsRedirection();

app.UseStaticFiles();

app.UseRouting();

app.UseAuthorization();

app.UseEndpoints(endpoints =\&gt;

{

endpoints.MapRazorPages();

});

}

}

Consider a basic page:

@page

\&lt;h1\&gt;Hello, world!\&lt;/h1\&gt;

\&lt;h2\&gt;The time on the server is @DateTime.Now\&lt;/h2\&gt;

The preceding code looks a lot like a [Razor view file](https://docs.microsoft.com/tr-tr/aspnet/core/tutorials/first-mvc-app/adding-view?view=aspnetcore-3.1) used in an ASP.NET Core app with controllers and views. What makes it different is the [@page](https://docs.microsoft.com/tr-tr/aspnet/core/mvc/views/razor?view=aspnetcore-3.1#page) directive. @page makes the file into an MVC action - which means that it handles requests directly, without going through a controller. @page must be the first Razor directive on a page. @page affects the behavior of other [Razor](https://docs.microsoft.com/tr-tr/aspnet/core/mvc/views/razor?view=aspnetcore-3.1) constructs. Razor Pages file names have a _.cshtml_ suffix.

A similar page, using a PageModel class, is shown in the following two files. The _Pages/Index2.cshtml_ file:

@page

@using RazorPagesIntro.Pages

@model Index2Model

\&lt;h2\&gt;Separate page model\&lt;/h2\&gt;

\&lt;p\&gt;

@Model.Message

\&lt;/p\&gt;

The _Pages/Index2.cshtml.cs_ page model:

using Microsoft.AspNetCore.Mvc.RazorPages;

using Microsoft.Extensions.Logging;

using System;

namespaceRazorPagesIntro.Pages

{

publicclassIndex2Model : PageModel

{

publicstring Message { get; privateset; } = &quot;PageModel in C#&quot;;

publicvoidOnGet()

{

Message += $&quot; Server time is { DateTime.Now }&quot;;

}

}

}

JSON Serialization And Deserialization In C#

[https://www.c-sharpcorner.com/article/json-serialization-and-deserialization-in-c-sharp/](https://www.c-sharpcorner.com/article/json-serialization-and-deserialization-in-c-sharp/)

MVC, MVP ve MVVM Patternleri

[https://denizirgin.com/mvc-mvp-ve-mvvm-patternleri-aa7d1011daff](https://denizirgin.com/mvc-mvp-ve-mvvm-patternleri-aa7d1011daff)
