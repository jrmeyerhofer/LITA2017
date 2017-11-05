# Lesson Seven - New Book List

In this lesson we'll create a new book list.

## Lesson Steps

1. Open Google Drive: https://drive.google.com
2. Create a new Google Sheet and name our file: "LITA 2017 New Book List (Lesson Seven)"
3. Copy this into your sheet (this is our pretend new book data):
<table>
  <thead>
    <tr>
      <th>ISBN</th>
      <th>Author</th>
      <th>Title</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>abc321465498</td><td>Zeus</td><td>The Big Book of Number 1s</td>
    </tr>
    <tr>
      <td>hij18842f532</td><td>Apollo</td><td>The Big Book of Stars</td>
    </tr>
    <tr>
      <td>lmn458137952</td><td>Athena</td><td>The Big Book of Long Ovals</td>
    </tr>
    <tr>
      <td>mno545558501</td><td>Demeter</td><td>The Big Book Vertical Ovals</td>
    </tr>
    <tr>
      <td>rst824713975</td><td>Poseidon</td><td>The Big Book of Rectangles</td>
    </tr>
    <tr>
      <td>xyz582528202</td><td>Hera</td><td>The Big Book of Polygons</td>
    </tr>
  </tbody>
</table>
4. Click on Tools menu and choose Script Editor.<br /> 
5. Copy in this code overwriting everything that is there:<br />
```javascript

function callImageSearch() {
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sheet = ss.getActiveSheet();
  
  var cell = sheet.getRange("D1");
  cell.setValue("ImageURL");
  
  var cell = sheet.getRange("E1");
  cell.setValue("RecordLink");
  
  //Loop through Column A, getting the ISBN numbers
  for (var i = 2; i < 500; i++) {
    
	var ISBNNumber = sheet.getRange(i,1).getValue();
	Logger.log('ISBNNumber: ' + ISBNNumber);
    
	// if the value is blank, no more ISBN Numbers! Break out!
	if (ISBNNumber == "") { break; }
        
        //example url: https://sites.google.com/meyerhofer.com/lita2017/home/mno545558501-html
	var ISBNURL = 'https://sites.google.com/meyerhofer.com/lita2017/home/' + ISBNNumber + '-html';
	var html = UrlFetchApp.fetch(ISBNURL).getContentText();
 
	if (html) {
  	  if (html.indexOf('CENy8b') >= 0) {
    	  // Image is present
    	  var locURL = html.indexOf('t3iYD');
    	  var locSpace = html.indexOf('CENy8b',locURL);
    	  var localURL = html.substring(locURL+17,locSpace-9)
  	  } else {
      	  var localURL = "No Image";
  	  }
	}
	Logger.log('locURL: ' +locURL);
	Logger.log('locSpace: ' +locSpace);
	Logger.log('localURL: ' +localURL);   

	var cell = sheet.getRange("D"+i);
	cell.setValue(localURL);
  
	var ISBNlinkcell = sheet.getRange("E"+i);
	ISBNlinkcell.setValue(ISBNURL);
    
	//clear the variables
	locURL = "";
	locSpace = "";
	localURL = "";

  }
}
//Run once to create the menu to run from the sheet!
function onOpen() {
  var ui = SpreadsheetApp.getUi();
  ui.createMenu('Scrape the Web')
  	.addItem('Get Image URLs from ISBN Numbers in col A','callImageSearch')
  	.addToUi();
}
```
6. This is the code we created from Lesson 6 but changed a little for our data. 
7. Save. *[Remember you may have to authorize your script.](../authorize.md)* Then manually run the onOpen function to create the menu.
8. Now you can run the custom menu function to get the image and record URL.
![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

## Final Google Sheet

https://docs.google.com/spreadsheets/d/1k21QDclGmK1YGOiyPuOUq4_QnISM4OXmVr1qfFgOxSg/edit?usp=sharing

## Resource list 

Main GAS documentation: https://developers.google.com/apps-script/

External APIs: https://developers.google.com/apps-script/guides/services/external

UrlFetchApp: https://developers.google.com/apps-script/reference/url-fetch/url-fetch-app
