# Lesson One - Getting Orientated

In this lesson we'll talk about what Google Apps Script (GAS) is, create our first script, and examine the development environment.

#### Google Apps Script:

Allows you to create add-ons for Google Sheets, Docs, Slides, or Forms, automate your workflow, integrate with external APIs, and more. It is JavaScript "like" and doesn’t need to be compiled. Because it's built into Google, you don't have to worry about hosting, backups, security, patching your server/application, or uploading files to a server.

What can you do? Add a menu to a sheet, build a stand-alone application, or create a container bound application in a Google Sheet or Docs. You can also run a GAS application as a web service - independ from interfaces - that can be called from elsewhwere on the web.

# Lesson Steps

1. Open Google Drive: https://drive.google.com
2. Create a new GAS file by clicking the New button -> More -> Google Apps Script
3. Note the Google Doc like environment. 
4. Name our file: LITA 2017 Test script (Lesson One)
5. Examine the File menu<br/>
"See Version History" is where you can see all the coding changes after a save.<br/>
"Manage Versions..." allows you to create versions of your code for deployment.<br/>
"Project Properties" contains detailed Google information about your project. Good to know it's there.<br/>
6. Examine the Edit menu<br/>
Triggers allow you to have the script run at a certain time or run based on an action - like when a Google Form is submitted.<br/>
7. Examine the View menu
8. Examine the Run menu
9. Examine the Publish menu
10. Examine the Resources menu
11. Let's add the following code deleteing what's there:
```javascript
function myFunction() {
  // put something into the logger.
  var myTestVar = "John is cool";
  Logger.log("myTestVar is: " + myTestVar);
}
```
12. Save the project and click the Run or play button.
13. This should prompt us to authorize our script. 

We'll - demo coding environment - You can watch as I walk through this or walk along with me.

Code can be added in the code editor and follows the Javascript syntax
Add code to get the Project property.

function myFunction() {
  // put something into the logger.
  var myTestVar = "John is cool";
  Logger.log("myTestVar is: " + myTestVar);
}

if we save, then run it then view the log. 
Talk about Run menu

Debug - just show, place a stop point - see information available. Screen print
View execution transcript

Talk about Publish, triggers? 

Resources menu: beyond scope of this session but just know about the advanced Google Services where you can and have to turn on other Google servieces to interface with them.

Maybe just explain: triggers now. Especially useful in Google Forms (show later?)

Somethings in first few lessons are just neat and I think if you know about them, you might be able to use them at your job.

# Resource list

Main GAS documentation: https://developers.google.com/apps-script/

Logger Service: https://developers.google.com/apps-script/reference/base/logger

Information about Troubleshooting/Debugger: https://developers.google.com/apps-script/guides/support/troubleshooting

GAS authorization: https://developers.google.com/apps-script/guides/services/authorization

