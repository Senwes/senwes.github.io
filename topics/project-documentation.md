---
layout: site
title: Project Documentation
body_class: process
---

Documentation is important for understanding the project at a higher level. This is where you can document decisions made about architecture, choice of external libraries and plugins, and process.

Generally speaking, long-lived documentation for a project should live within the project repository in the form of markdown files. This ensures that all documentation is version-controlled along with the project, and any changes needed to documentation can be done as part of a pull request on the project.

As a standard, projects should also contain READMEs at the project root level. These READMEs should lay out the basics of getting started with the project (i.e. instructions for installation and workflow), and no other information. Examples:

* How to build the project
* If it is a deployable, how to run it
* If it is a library, a quickstart on how to use it
* If it has an API, a link to more detailed API documentation

Additional meta information about the project not specifically intended for engineers can be located in a project wiki in Confluence and linked.

* Use [Miro](https://miro.com/login/){:target="_blank"} to create ERD, process flow and other project documentation.
* Add the BVP (from the user), the functional spec (from the Business Analyst) and Technical Spec (from the development team), the blank template can be downloaded [here](https://senwes.sharepoint.com/:w:/r/sites/KnowledgeBase909/Applications/General/Templates/Technical%20Spec%20Blank.docx?d=w210a2c4eff794553a7790f17f50db0db&csf=1&web=1&e=4qIf1X){:target="_blank"}.

### APIs

Public APIs should have a page describing how to use the API. These documents should at a minimum include all publicly available calls, details on how to use authentication and example response and request formats.
