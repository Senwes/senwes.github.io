---
layout: site
title: Service Standards and Naming Conventions
body_class: code
---

Make sure to read the [Handbook Extension: Services](https://senwes.visualstudio.com/Applications/_wiki/wikis/Applications.wiki/24/Engineering-Handbook-Extension-Services){:target="_blank"}.

### Services (Services always end with xxx.Service)
Always use a solutions folder if it does not already exist.
All Services are suffixed with dotService in order to make finding the actual DLL easy within a solution.

### Structure
* Layered Architecture. Click [here](https://miro.com/app/board/uXjVPaY7IB4=/?share_link_id=528900992742){:target="_blank"} to view or update this structure in Miro.
![image info](../images/Applications Architecture.jpg)
* Our policy is each service does one thing and one thing well. 
* The service business logic will not be repeated. Even though the Core project is available across services. 
* All services will return a DTO and never an entity. The entity itself is shielded from the controller. A DBcontext cannot be initialized from the Business layer. 
* Use caching in instances where common data is queried and does not change much. 
* Use relationships so that you limit DB connections. 

### Caching
* In-Memory Cache in dotNet:
1. Caching can be done using inline caching or cache action filters. Example of these can be found in the Globalntegration > Helpers > Filters Folder
* For Angular caching, read [this](https://baldur.gitbook.io/angular/rxjs/rxjs/sharereplay){:target="_blank"} related article on ShareReplay.
* Please take precaution when using caching. Refresh/Delete the cache when data changes etc.


### Service Solutions contains the following projects
* <i>Solution</i>.Service.API
> Controllers
* <i>Solution</i>.Service.Business
> Business Logic related only to this project
* <i>Solution</i>.Service.Data
> DbContext
> Model Enitities
> Unit of Work
* <i>Solution</i>.Service.Dto
> Classes correcponding to enities in Model Enitities
* <i>Solution</i>.Service.Integration
> All calls to external Services (Preferred method: fluently)
* <i>Solution</i>.Service.UnitTests
> Create unit tests per model entity 

### General
* Always prefer meaningful names for your class, property, method, etc. This will be very useful for you to maintain the code in future.
* Never have a different class or variable name that is in a different case. 
> Example: <i>Entity</i> and <i>entity</i>.
* Don't use the same name used in .NET Framework. Developers who are new to your code have great difficulty to understand it easily.
* Always use “I” as prefix for Interfaces. This is a common practice for declaring interfaces.
> Example: I<i>Entity</i>.cs
* Never prefix or suffix the class name to its property names. It will unnecessarily increase the property name. If “Firstname” is a property of <i>Entity</i> class, you can easily identify it from that class directly. No need to write <i>Entity</i>Firstname or FirstnameOf<i>Entity</i>.
* The prefix “Is”, “Has” or “Can” for boolean properties like these give proper meaning to the properties.
> Example: 
>> IsVisible <br />
>> HasChildren <br />
>> CanExecute <br />
* <b>Private variables</b> start with an underscore.
> Example: private bool _IsVisible;
* <b>Paramenters</b> must be descriptive (<b>do not use</b>: int value) and start with lowercase then pascalCase.
> Example: (int <i>entity</i>Number)
* <b>Methods</b> give descriptive names as simple as possible. Starts with capital letter, then pascalCase. 
> Example: Get<i>Entity</i>(int <i>entity</i>Number)
* When a method has a return value that will not be used, use discards, this enhance its readability and maintainability. [Discards - C# Fundamentals](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/discards){:target="_blank"}
* Always use curley brackets {} for if, switch, for, etc statements, even if it has only one line of code.
