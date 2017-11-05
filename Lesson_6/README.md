# Lesson Five - Scraping the web

In this lesson we'll learn how to scrape a website. We are going to scrape a fake catalog for book cover images. This is so we don't overload any of the real catalogs and possibliy make them block us. Here is the Fake Book Site: https://sites.google.com/meyerhofer.com/lita2017/home 

## Lesson Steps

1. Open Google Drive: https://drive.google.com
2. Create a new Google Sheet and name our file: "LITA 2017 Scrape (Lesson Six)"
3. Copy this into your sheet (these are our pretend ISBNs):
```
abc321465498
hij18842f532
lmn458137952
mno545558501
rst824713975
xyz582528202
```
4. Click on Tools menu and choose Script Editor. 
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

	var cell = sheet.getRange("B"+i);
	cell.setValue(localURL);
    
	var image = '=image(B' + i + ',4,90,70)';
	var imagecell = sheet.getRange("C"+i);
	imagecell.setValue(image);
    
	var ISBNlinkcell = sheet.getRange("D"+i);
	ISBNlinkcell.setValue(ISBNURL);
    
        // Sets the row to a height of 100 pixels so we can see the image
	sheet.setRowHeight(i, 100);

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
![Image of images](images.png)
8. Let's look at the code to see what it's doing:<br />
First, we get the active sheet, and loop through the ISBN numbers in col A. Then we get the URL and fetch it.
```
var ISBNURL = 'https://sites.google.com/meyerhofer.com/lita2017/home/' + ISBNNumber + '-html';
var html = UrlFetchApp.fetch(ISBNURL).getContentText();
```
With the entire HTML page in a variable, we can search for the specific string which will mark the image file.
```
var locURL = html.indexOf('t3iYD');
var locSpace = html.indexOf('CENy8b',locURL);
var localURL = html.substring(locURL+17,locSpace-9)
```
This is a perfect example why scraping a website is an inexact science! With the URL, we write out the data and image into the sheet.<br /><br />
9. **Excersize (15 min):** Get the image url from http://www.worldcat.org/title/little-life-a-novel/oclc/886672369. Some tips: Google Dev Tools can help find or select HTML elements. Find a unique tag or string before and after the image url. For example, in the previous steps, we used the dev tools to find the image url:<br /><br />
![Image of isbn](isbn.png)<br /><br />
Then looked for a unique string before and after the image URL:<br /><br />
![Image of tags](tags.png)


<br /><br /><br /><br /><br /><br /><br /><br />
code, get first image? they do others? code should loop? feed from ISBNs?

remember be good about scrapign websites! scrapign an exact science. APIs better!

inline linking? 

challenge: https://www.googleapis.com/books/v1/volumes?q=oclc:886672369 
google book api?

10. **Excersize (5 min):** Try other DOIs. Do you always get the same values back? What's different? Why is it different? Ready more about oaDOI's API DOI object: https://oadoi.org/api/v2#doi-object
11. **Excersize (10-15 min):** Expand your script to get other individual values from the JSON string. Can you get the URL value?
12. **Challenge Excersize (10 min):** Can you call the [Crossref API](https://github.com/CrossRef/rest-api-doc) and extract its data? Example: https://api.crossref.org/works/10.1037/0003-066X.59.1.29

**Note: This is just one of the many APIs you can call from GAS. In some cases you may need a [key](https://en.wikipedia.org/wiki/Application_programming_interface_key) to performa a call. More APIs can be found at https://apilist.fun/ and https://github.com/toddmotto/public-apis.**

## Final Google Sheet

https://docs.google.com/spreadsheets/d/1k21QDclGmK1YGOiyPuOUq4_QnISM4OXmVr1qfFgOxSg/edit?usp=sharing

## Resource list

Main GAS documentation: https://developers.google.com/apps-script/

UrlFetchApp: https://developers.google.com/apps-script/reference/url-fetch/url-fetch-app

Free Images: https://unsplash.com/photos/rMYrkFfw36U
