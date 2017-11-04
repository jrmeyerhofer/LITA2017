# Lesson One - Getting Orientated

In this lesson we'll talk about what Google Apps Script (GAS) is, create our first script, and examine the development environment.

# Google Apps Script:

Allows you to create add-ons for Google Sheets, Docs, Slides, or Forms, automate your workflow, integrate with external APIs, and more. It is JavaScript "like" and doesn’t need to be compiled. Because it's built into Google, you don't have to worry about hosting, backups, security, patching your server/application, or uploading files to a server.

What can you do? Add a menu to a sheet, build a stand-alone application, or create a container bound application in a Google Sheet or Docs. You can also run a GAS application as a web service - independ from interfaces - that can be called from elsewhwere on the web.

# Steps

1. Open Google Drive: https://drive.google.com
2. Create a new GAS file by clicking the New button -> More -> Google Apps Script
3. Note the Google Doc like environment. 
4. Name our file: LITA 2017 Test script (Lesson One)
5. Examine the File menu
  Note: See Version History where you can see all the coding changes after a save
        Manage Versions...
        Project Properties

6. Examine the Edit menu
7. Examine the View menu
8. Examine the Run menu
9. Examine the Publish menu
10. Examine the Resources menu



Show version control, 

We'll - demo coding environment - You can watch as I walk through this or walk along with me.

Basic file menu, just like google docs we can give our file a name.
We also have version control in GAS. We can create a new version. This is helpful for releases of code or just managing your code.

Code can be added in the code editor and follows the Javascript syntax
Add code to get the Project property.

function myFunction() {
  // put something into the logger.
  var myTestVar = "John is cool";
  Logger.log("myTestVar is: " + myTestVar);
}
//Main Google Apps Script site: https://developers.google.com/apps-script/
//Logger Service: https://developers.google.com/apps-script/reference/base/logger
//Information about Troubleshooting/Debugger: https://developers.google.com/apps-script/guides/support/troubleshooting

if we save, then run it then view the log. 
Talk about Run menu

Debug - just show, place a stop point - see information available. Screen print
View execution transcript

Talk about Publish, triggers? 

Resources menu: beyond scope of this session but just know about the advanced Google Services where you can and have to turn on other Google servieces to interface with them.

Maybe just explain: triggers now. Especially useful in Google Forms (show later?)

Somethings in first few lessons are just neat and I think if you know about them, you might be able to use them at your job.

# Resource list

https://developers.google.com/apps-script/
Main Google documentation and help for Google Apps Script
