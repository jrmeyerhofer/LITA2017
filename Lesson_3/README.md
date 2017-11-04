# Lesson Three - Create custom menus

In this lesson we'll create a custom menu and a clickable button in a Google Sheet.

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
```
5. Save and name your script. This code will add a custom menu to our sheet. 
6. Manually run the XXXXX function. If you look at your sheet, you will now have a new menu.<br /><br />
![Image of Menu](custom_menu.png)

click on menu and it runs the appropriate funtion:<br /><br />
![Image of Popup](popup.png)




has created a basic function that takes in some input and then returns that input with the string " is cool" appended to it. 
6. Let’s take a look at what it does in our sheet. Leave the script file open and go back to your GSheet tab. Enter in your first name into the A1 cell. Then in the B1 cell enter:
```=addCooltoString(A1)```
7. Tab off the cell. This will take your name and add “ is cool” to it.<br /><br />
![Image of step 5](is_cool.png)
8. Excersize (5-10min): Create a function that will take in a whole number and add 2 more than that number to it. *I bet you didn’t know there was going to be Math during this session did you!* So, if we have 5, our new function would be 5 + 7 or 12.

## Final Google Sheet

https://docs.google.com/spreadsheets/d/1wb8yw8zWIOyGSxPgmZvbjonZh9gImeLjYUs7E0ibP_w/edit?usp=sharing

## Resource list

Main GAS documentation: https://developers.google.com/apps-script/

Custom Menus: https://developers.google.com/apps-script/guides/menus

Simple Triggers: https://developers.google.com/apps-script/guides/triggers/



Next we’ll Create some custom menus 
Open a new Google Doc and title it Lesson Two Menu LITA
Click on the Tools Menu and open the Script Editor
Open this gist code - link - and copy it into the script editor.
Save and name your script file.
So before we run this let’s look through the code and see what it’s going to do.
You’ll see the first function, onOpen. This is a special function in Google Apps Script. It is a simple triggers which executes when a user opens a Google Docs, Sheets, or Forms file. There are others which you can read about in the resources. 
First it gets the document, then it adds a menu called Custom Menu. Then it adds 'First item' to the menu, then a Separator, then a submenu with an item, finally it actually adds it to the Document. Also note that during each of the adds, a function is being associated to that menu item. So if I click on Second item that will trigger menuItem2. 
Now rather than close the document and re-open, I’ll show you another way you can manually run a function from within the apps script developer. 
From the dropdown choose the onOpen function then click the play button. This will manually run the function. Ok, who got an error? I got an error. All of you should have got an error, and that’s ok. I did this on purpose to show you what will happen when you get an error. Usually its a small red box at the top that isn’t very helpful. But this time, we see that it is and is telling us that it can call this one function SpreadsheetApp.getUi(); That’s because it is only for Google Sheets. So now everyone change SpreadsheetApp to DocumentApp and save, and run it again. Hopefully this time it ran successful and you didn’t get any errors. Everyone ok?
Now let’s swap over to our Google Doc and you should see a new menu item. Go ahead and click on one of them and see what happens. You should see the dialog box pop up. 



