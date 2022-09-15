---
layout: site
title: Code Standards
body_class: code
---

The following checklist should be applied when conducting a [Code Review](code-reviews.html).

### Introduction

Senwes Applcations strive for readability, consistency, innovation, scalability and forward thinking in development. 
Code Formatter 
Use the formatter that Visual studio has to format your code. This will add the needed space and improve readability.
*	When using Visual Studio the shortcut will be: 
*	Ctrl+K+D.
*	When using Visual Studio Code the shortcut will be: 
*	Ctrl+A then Ctrl+K+F
*	Shift+Alt+F

### Security

* Code should never contain credentials. These are a property of the environment.
* Is the new code opening up a vulnerability? We should all be aware of methods of attack - such as those identified by OWASP[^1].
* Assets should be loaded with a HTTPS URL wherever possible.

Senwes Applications policy is everything is secured unless otherwise stated.
* We use token-based security on Microservices. 
* 2 Tokens are created - System and Expiration token. Each request within a time frame has a token which expires and cannot be used again. 
* All communication to microservices is secured with SSL. 
* Tokens are encrypted using SQL encryption and C# based encryption for Expiration Tokens as these are not stored in the DB.
* We used a scaled down token for certain methods/actions where only a token is passed in as from SAP.

### Layered Architecture
* Click [here](https://miro.com/app/board/uXjVPaY7IB4=/) to view or update this structure.

### General

* <b>Spelling correctly is crutial.</b>
* [Naming Conentions](naming-conventions.html)
* Object-Oriented Analysis and Design (OOAD) Principles
1.	Single Responsibility Principle (SRS): Do not place more than one responsibility into a single class or function, refactor into separate classes and functions.
2.	Open Closed Principle: While adding new functionality, existing code should not be modified. New functionality should be written in new classes and functions.
3.	Liskov substitutability principle: The child class should not change the behavior (meaning) of the parent class. The child class can be used as a substitute for a base class.
4.	Interface segregation: Do not create lengthy interfaces, instead of splitting them into smaller interfaces based on the functionality. The interface should not contain any dependencies (parameters), which are not required for the expected functionality.
5.	Dependency Injection: Do not hardcode the dependencies, instead inject them.

* Fix any broken windows. They are not someone else’s problem. See [Out Charter](charter.html). However, please be respectful of your colleagues when doing this.
* The repository/project should be Continuously Integrated - see [Continuous Integration](continuous-integration.html) for specifics.
* The code should compile and run without error.
* No commented out code blocks. Source control has history for a reason.
* Look out for spelling mistakes, both in user text and also code itself
* Debug statements to the console (e.g. `echo, var_dump, System.out.print, console.log`) should be removed. Use debug logging instead.
* Check for adequate logging. If you were personally supporting this pull request on your own after merging, you should be satisfied with the level of debug.
* Similarly check that adequate analytics have been added (where appropriate).
* Ensure code is defensive.
* If signatures of functions have changed, check for redundant variables. Also, does the documentation block for the function correctly reflect its intended function and the parameters it accepts and values it returns.
* If introducing a new external dependency, the appropriate version should be locked on to, rather than using fuzzy versioning.
* Pick up issues that could/should have been picked up by a linter. If there is no linter, ask for one to be added. [Super Linter](https://github.com/github/super-linter/blob/master/README.md).
* Don’t allow new TODOs without referencing an open issue for discussion.

### Technical debt and “fixing broken windows”

Technical debt[^2] refers to aspects of a codebase that are known to be problematic, but are introduced to facilitate some other goal - usually faster delivery.

The metaphor is supposed to draw on how real-life debt works:

* a loan is a useful tool to facilitate an otherwise unattainable goal;
* debt comes with a cost: you pay interest on the debt;

Technical debt can be classified by the “interest rate” applied to repayments: a known problem that never affects us has low interest; one that affects us every day - e.g. manual labour on every code-review, or every release - has high interest. The interest rate is a useful way to classify and prioritise our technical debt.

“Broken windows” refers to small issues that we notice as we are working within a codebase, but that are not strictly part of the work we are doing. Examples of broken windows are:

* Typos and spelling mistakes
* Newly uncovered bugs
* Code smells (see next section)
* Outdated dependencies

We should - per our charter - fix broken windows, so that our code is improving continuously. However, there is a tension in doing this.

Code review is a vital part of our process, and consumes our time and our colleagues’ time. Large pull-requests take a long time to review, and complexity makes this worse. We want to keep pull-requests small and simple.

If we fix broken windows in functional-change pull-requests, we increase the size and complexity of our pull-request, as the functional changes cannot be easily disentangled from refactoring changes.

This is a classic case of interest payment on our technical debt. Therefore, we would recommend separating “broken window” fixes from functional-changes. This is not always easy, so we offer the following strategies.

First, if you know which files you are likely to change, and are concerned that those files have broken windows, issue a pull-request to fix those broken windows before starting the functional work.

Second, if you don’t know which files you will touch, we would recommend leaving the broken windows broken in your functional-change pull-request, then - once it is merged - issue a follow-up pull-request to fix the broken windows.

Third, if you absolutely must combine broken window fix and functional changes in the same pull-request, please perform a code-review yourself before submitting it to your peers, commenting on every single instance of refactoring or fixing, to explain why they have been changed, and that they are not related to the functional changes.

Finally, if you find yourself manually fixing the same kind of broken window in every pull-request, stop doing it. Find an automated way to resolve the issue (e.g. a linter) if you can, and agree a strategy for rolling out that same fix across the codebase with the rest of the team.

None of these are hard-and-fast rules; we recommend being mindful of the effect of our changes on others.

### Code smells[^3]

* Repetitive code - DRY[^4]
* Large classes
* Poor separation of concerns[^5]
* Badly-named files or classes
* Undefined, badly-named, or redundant variables
* Unnecessary code where a command might do the trick
* Does the code look complicated and is it hard to understand? KISS.[^6]
* Use constants
* // Are there enough comments in the code?

### Performance

We need to be mindful of how our applications perform on many levels. We should look for changes that adversely affect response times, as well as any other negative effects the new code might have. Amongst other things, look for:

* Inefficient database queries
* Missing indexes on databases
* Infinite loops/recursion
* Opportunities to break out of a loop early when appropriate
* Opening up connections to database/other services and not closing them
* Incorrect callback names (as appropriate) - or callbacks triggered too early
* Situations where a callback is made but code can continue to execute after this point - with unintentional consequences

### Tests

* Ensure there are appropriate tests (unit/integration/browser). See [Testing](testing.html) for more specifics.
* Tests that rely on external services can result in failing tests. Use a mock/stub/spy.
* Tests should be atomic and pass if they are run singularly or part of the suite. They should never depend on being run in a specific order or rely on the output of another test.
* Waiting for elements on a page during browser tests is much preferred to sleep commands.
* Do not mock the system under test. Exceptions are only allowed when the system under test gets its external services via `getXXX` methods (but we should avoid this, preferring dependency injection).

### Documentation

There should be living documentation - project READMEs, API documentation (if applicable), wiki pages, and/or infra runbooks. Ensure these are kept up-to-date in code changes. See [Project Documentation](project-documentation.html) for more specifics.

[^1]: [OWASP Top-Ten](https://owasp.org/www-project-top-ten/)
[^2]: [Technical debt](https://en.wikipedia.org/wiki/Technical_debt)
[^3]: [Code smells](https://sourcemaking.com/refactoring/smells)
[^4]: [Don’t repeat yourself - DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
[^5]: [Separation of Concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)
[^6]: [KISS principle](https://en.wikipedia.org/wiki/KISS_principle)
