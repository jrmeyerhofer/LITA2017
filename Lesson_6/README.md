# Lesson 6 - Scraping the web

In this lesson we'll learn how to scrape a website. We are going to scrape a fake catalog for book cover images. This is so we don't overload any 'real' catalogs and possibly make them block us. Here is the Fake Catalog Site: https://fakecatalog.wordpress.com/ 

## Lesson Steps

1. Open Google Drive: https://drive.google.com
2. Create a new Google Sheet and name our file: "LITA 2017 Scrape (Lesson 6)"
3. Copy this into your sheet in cells A1:A6 (these are our pretend ISBNs):
```
abc321465498
hij18842f532
lmn458137952
mno545558501
rst824713975
xyz582528202
```
4. Click on the Tools menu and choose Script Editor. 
5. Copy in this code overwriting everything that is there:
```javascript
function callImageSearch() {
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sheet = ss.getActiveSheet();
 
  //Loop through Column A, getting the ISBN numbers
  for (var i = 1; i < 500; i++) {
    
	var ISBNNumber = sheet.getRange(i,1).getValue();
	Logger.log('ISBNNumber: ' + ISBNNumber);
    
	// if the value is blank, no more ISBN Numbers! Break out!
	if (ISBNNumber == "") { break; }
        
        //example url: https://fakecatalog.wordpress.com/hij18842f532/
	var ISBNURL = 'https://fakecatalog.wordpress.com/' + ISBNNumber + '/';
	var html = UrlFetchApp.fetch(ISBNURL).getContentText();
    
	if (html) {
  	  if (html.indexOf('zfr3Q JYVBee') >= 0) {
    	  // Image is present
    	  var locURL = html.indexOf('zfr3Q JYVBee');
    	  var locSpace = html.indexOf('img',locURL);
    	  var localURL = html.substring(locURL+23,locSpace-3)
  	  } else {
      	  var localURL = "No Image";
  	  }
	}
	Logger.log('locURL: ' +locURL);
	Logger.log('locSpace: ' +locSpace);
	Logger.log('localURL: ' +localURL);   

	var cell = sheet.getRange("B"+i);
	cell.setValue(localURL);
    
	var image = '=image(B' + i + ',1)';
	var imagecell = sheet.getRange("C"+i);
	imagecell.setValue(image);
    
	var ISBNlinkcell = sheet.getRange("D"+i);
	ISBNlinkcell.setValue(ISBNURL);
    
        // Sets the row to a height and width so we can see the image
	sheet.setRowHeight(i, 200);
        sheet.setColumnWidth(3, 175);

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
6. Save. *[Remember you may have to authorize your script.](../authorize.md)* Then manually run the onOpen function to create the menu.
7. Back in the sheet, run the new menu option to Scrape the Web. You should see this:<br /><br />
![Image of images](bookimages.png)
8. Let's look at the code to see what it's doing:<br />
First, we get the active sheet, and loop through the ISBN numbers in col A. Then we get the URL and fetch it.
```
var ISBNURL = 'https://fakecatalog.wordpress.com/' + ISBNNumber + '/';
var html = UrlFetchApp.fetch(ISBNURL).getContentText();
```
With the entire HTML page in a variable, we can search for the specific string which will mark the image file.
```
var locURL = html.indexOf('zfr3Q JYVBee');
var locSpace = html.indexOf('img',locURL);
var localURL = html.substring(locURL+23,locSpace-3)
```
This is a perfect example why scraping a website is an inexact science and APIs are a much better option! We can write out the image URL and item URL into the sheet.<br /><br />
9. **Excersize (15 min):** Get the image url from http://www.worldcat.org/title/little-life-a-novel/oclc/886672369. Some tips: Google Dev Tools can help find or select HTML elements. Find a unique tag or string before and after the image url. For example, in the previous steps, we used the dev tools to find the image url:<br /><br />
![Image of isbn](google_dev.png)<br /><br />
Then looked for a unique string before and after the image URL:<br /><br />
![Image of tags](find_code.png)
<br /><br />
*Remember: Web scraping puts a large workload on a targeted server and this can upset the data holder. Be polite and time your requests to add a delay between server hits. And check for an API first!*

## Final Google Sheet

https://docs.google.com/spreadsheets/d/10B6sOAaJeiwFKPTQyzoV87oLRwBZUA0ogrvLazU2JHw/edit?usp=sharing
*Don't try to run this script, you'll get an [error](../autherror.png). Copy the code and run it in your own Google Drive.*

## Resource list

Main GAS documentation: https://developers.google.com/apps-script/

UrlFetchApp: https://developers.google.com/apps-script/reference/url-fetch/url-fetch-app

Free Images: https://unsplash.com/photos/rMYrkFfw36U

## Lessons

[Lesson 1 - Getting Orientated](/Lesson_1/)<br />
[Lesson 2 - Create your own function](/Lesson_2/)<br />
[Lesson 3 - Create a custom menu](/Lesson_3/)<br />
[Lesson 4 - Sidebar](/Lesson_4/)<br />
[Lesson 5 - Calling APIs](/Lesson_5/) **(PREVIOUS)**<br />
[Lesson 6 - Scraping the web](/Lesson_6/)<br />
[Lesson 7 - Building a New Book page](/Lesson_7/) **(NEXT)**<br />
[Lesson 8 - Web App](/Lesson_8/)
