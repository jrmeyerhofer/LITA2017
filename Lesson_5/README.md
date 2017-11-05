# Lesson Five - Calling APIs

In this lesson we'll learn how to call APIs from a Google Apps Script and call the XXXX API.

## Lesson Steps

1. Open Google Drive: https://drive.google.com
2. Create a new Google Sheet and name our file: "LITA 2017 Custom Menu (Lesson Three)"
3. Click on Tools menu and choose Script Editor. 
4. Copy in this code overwriting everything that is there:
```javascript
function onOpen() {
  var ui = SpreadsheetApp.getUi();
  // Or DocumentApp or FormApp.
  ui.createMenu('Our Custom Menu')
      .addItem('First Menu', 'menuOne')
      .addSeparator()
      .addSubMenu(ui.createMenu('SubMenu')
          .addItem('Second Menu', 'menuTwo'))
      .addToUi();
}
function menuOne() {
  SpreadsheetApp.getUi() // Or DocumentApp or FormApp.
     .alert('You clicked the first menu item!');
}
function menuTwo() {
  SpreadsheetApp.getUi() // Or DocumentApp or FormApp.
     .alert('You clicked the second menu item!');
}
function buttonClick() {
  SpreadsheetApp.getUi() // Or DocumentApp or FormApp.
     .alert('You clicked the button!');
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

https://docs.google.com/spreadsheets/d/1lWE6zxqOta44FM5m7-oHTPFjBbP1fnTDIaKQth1fb78/edit?usp=sharing

## Resource list

Main GAS documentation: https://developers.google.com/apps-script/

Custom Menus: https://developers.google.com/apps-script/guides/menus

Simple Triggers: https://developers.google.com/apps-script/guides/triggers/
