RestAPI-TestSample-soapui-project

1. Project tests a real online tool used for project management called 'Asana'. See https://www.asana.com/
   In 'Asana' teams which work in specified workspaces create different projects and perform some tasks.
   More detailed description of Asana tool avalaiable at https://developers.asana.com/docs/object-hierarchy  
   API docs available at https://developers.asana.com/docs
   Here I mainly used requests relating to 'projects' which are documented at https://developers.asana.com/docs/projects

2. Projekt description:
   Project uses basic CRUD methods: POST, READ, PUT, DELETE and OAuth2 authentication.
   'Get mutliple workspaces' request is run first to obtain current 'workspace ID' that is next used in furhter requests (POST, PUT, READ).

   Project is supposed to test possibility of creating a new project in current workspace, its update and finally deletion.
   'GET ALL PROJECTS...' request is run after each operation to verify current project list.

   Data for consecutive requests are passed from so called Properties (variables) or from other request's responses
   via PropertyTransfer steps or GroovyScripts.

   'GET ALL PROJECTS after POSTing a new one' request contains differnt assertion examples. 
   Also 'Script Assertion' checking one of the response's nodes is present there.  

3. The purpose of this simple 'end-to-end' project is to present some basic SoapUI REST API testing skills that I acquired during my 
   online tutorial self-studying  

4. Scope of knowledge:
   - Creating Project, Test Suite, Test Case, Test Step (PropertyTransfer, Grovy Script, Property Step)
   - Creating and accessing Properties (variables) at different levels (Project, Test Suite)
   - Creating simple Groovy Scripts. Passing Parameters between requests/steps: 
     > Using JsonSlurper class to parse request/response.
     > Using JsonBuilder class to build JSON object.
     > Using testRunner class to access Properties (variables) at different levels.
     > Using JsonPath to access nodes.
   - Using 'Property Transfer' step to pass Parameters between requests.
   - Creating basic assertions (Contains, Valid/Invalid HTTP Status Codes, ResponseSLA, JsonPath Match/Existence Match/Count, etc.)
   - Creating basic Script Assertions:
     > Using messageExchange class to access 'responseContent'
     > Using context class to access properties at different levels (e.g. TestCase)
 
Please note that in 'Delete a project' request, method chenges from DELETE to PUT each time SoapUI is reopened.
I suppose this might be due to some sort of SoapUI bug.
After correcting that (setting method back to DELETE) also 'ProjectIDTransfer' needs to be refreshed: 'project_gid' should be 
sellected from the 'Property' list in 'Target' section.
After this correction, all works fine End-to-End.
      