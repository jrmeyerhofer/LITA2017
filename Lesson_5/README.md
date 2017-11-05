# Lesson Five - Calling APIs

In this lesson we'll learn how to call APIs from a Google Apps Script and call the oaDOI API.

## Lesson Steps

**Background:** Open this URL in a browser window: https://api.oadoi.org/10.1088/0004-637x/812/2/158. This has called the oaDOI API (https://oadoi.org/api) returning JSON data about that DOI. This API gives us access to oaDOI's data about DOIs and their details. We are going to create a simple application that will take a DOI input, call the oaDOI API and then display the data we get back.

1. Open Google Drive: https://drive.google.com
2. Create a new Google Sheet and name our file: "LITA 2017 API (Lesson Five)"
3. Click on Tools menu and choose Script Editor. 
4. Copy in this code overwriting everything that is there:
```javascript
function getOAAPIDOI()
{
    var ss = SpreadsheetApp.getActiveSpreadsheet();
    var sheet = ss.getActiveSheet();
  
    //Status: Intialize
    var cell = sheet.getRange("B1");
    cell.setValue("STATUS: Starting...");
    
    var email_key = 'youremail@test.com'; 
    var DOInumber = sheet.getRange("A1").getValue();
    DOInumber = DOInumber.trim();
    var cell = sheet.getRange("A1");
    cell.setValue(DOInumber);
    
    //Status: Calling OADOI API
    var cell = sheet.getRange("B1");
    cell.setValue("STATUS: Calling OADOI API...");
    
    //example of what the URL of a call would look like. Could put this into a browser window and see the JSON:
    //https://api.oadoi.org/10.1088/0004-637X/802/1/66
    var doiJSON = 'https://api.oadoi.org/' + DOInumber + '?email=' + email_key;
    Logger.log('doiJSON: ' + doiJSON);
    
    // Make request to API and get response before this point.
    var json = UrlFetchApp.fetch(doiJSON);
    Logger.log('json: ' + json);
    var response = json.getContentText();
    Logger.log('response: ' + response);
    var data = JSON.parse(response);
   	
    //put out the whole JSON string
    var cell = sheet.getRange("A3");
    cell.setValue(response);
  
    //doi - 5
    if ('doi' in data['results'][0]) {
      var doi = data['results'][0]['doi'];
      Logger.log('doi: ' + doi);
      var cell = sheet.getRange("A5");
      cell.setValue("doi");
      var cell = sheet.getRange("B5");
      cell.setValue(doi);
    }
 
    //Status: Done
    var cell = sheet.getRange("B1");
    cell.setValue("STATUS: Done!");
}
//Create the menu to run from the sheet
function onOpen() {
  var ui = SpreadsheetApp.getUi();
  ui.createMenu('Call OA API')
      .addItem('Use DOI in cell A1 to call API','getOAAPIDOI')
      .addToUi();
}
```
8. First, you'll see something familar. The onOpen function that will create a custom menu for us to run from our sheet. 
9. Manually run the onOpen function to create the menu.
10. The other code is new, so let's walk through it:
This code gets the active sheet, then sets the value of cell B1. This is a nice way to see visually what the code is doing.
```javascript
    var ss = SpreadsheetApp.getActiveSpreadsheet();
    var sheet = ss.getActiveSheet();
    var cell = sheet.getRange("B1");
    cell.setValue("STATUS: Starting...");
```
Here we are getting the value of cell A1, which should have our DOI, and making sure it doesn't have any spaces before or after it.
```javascript
    var DOInumber = sheet.getRange("A1").getValue();
    DOInumber = DOInumber.trim();
    var cell = sheet.getRange("A1");
    cell.setValue(DOInumber);
```
This code pieces together our URL then uses teh URLFetch to open it and puts the JSON string into a variable.
```javascript
    var doiJSON = 'https://api.oadoi.org/' + DOInumber + '?email=' + email_key;
    var json = UrlFetchApp.fetch(doiJSON);
    var response = json.getContentText();
    var data = JSON.parse(response);
```
We then put that JSON string in the A3 cell.
```javascript
    var cell = sheet.getRange("A3");
    cell.setValue(response);
```
Finally, we navigate the JSON file, and get the value of the doi and put it in cell A5
```javascript
    if ('doi' in data['results'][0]) {
      var doi = data['results'][0]['doi'];
      var cell = sheet.getRange("A5");
      cell.setValue("doi");
      var cell = sheet.getRange("B5");
      cell.setValue(doi);
    }
```





5. Save and name your script. This code will add a custom menu to our sheet with a menu item and a sub-menu. You can see where it designates the name and then the function that will run when that menu is clicked. 
6. Manually run the onOpen() function. *Note: onOpen() is a special function called a simple trigger and will normally run when a user opens a spreadsheet, document, or form.* If you look at your sheet, you will now have a new menu.<br /><br />
![Image of Menu](custom_menu.png)
7. Click on one of the menus and it will run the appropriate funtion - *menuOne() or menuTwo()*:<br /><br />
![Image of Popup](popup.png)
8. **Excersize (5 min):** Create another menu item and put it anywhere in your menu. *Make sure to create a function that gets triggered when it runs!* Rather then re-run the onOpen function manually, what happens if you save the script, close your sheet and then open it back up?
9. You can also assign a function to an image or drawing. Back in our sheet, click the Insert -> Drawing menu. Add a rectangular shape to our sheet. 
10. Click on the three veritcal dots to Assign a Script *Tip: enter the function without the parens like "buttonClick"<br /><br />
![Image of assign](assign.png)
10. **Excersize (5 min):** Add an image to your sheet and assign a funtion to it. *Tip: easily add an image by URL: https://source.unsplash.com/random*

## Final Google Sheet



## Resource list

Main GAS documentation: https://developers.google.com/apps-script/

External APIs: https://developers.google.com/apps-script/guides/services/external

UrlFetchApp: https://developers.google.com/apps-script/reference/url-fetch/url-fetch-app
