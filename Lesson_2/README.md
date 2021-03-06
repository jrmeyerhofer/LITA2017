# Lesson 2 - Create your own function

In this lesson we'll create our own function in a Google Sheet.

## Lesson Steps

1. Open Google Drive: https://drive.google.com
2. Create a new Google Sheet and name our file: "LITA 2017 Custom Function (Lesson 2)"
3. Click on the Tools menu and choose Script Editor - This opens a script file that is associated with the sheet we just created. This is what’s called a bound script. 
>“A script is bound to a Google Sheets, Docs, or Forms file if it was created from that document rather than as a standalone script. The file a bound script is attached to is referred to as a "container". Bound scripts generally behave like standalone scripts except that they do not appear in Google Drive, they cannot be detached from the file they are bound to, and they gain a few special privileges over the parent file.”
4. Copy in this code overwriting everything that is there:
```javascript
function addCooltoString(input) {
   return input + " is cool";
}
```
5. Save and name your bound script. This code has created a basic function that takes in some input and then returns that input with the string " is cool" appended to it. *[Remember you may have to authorize your script](../authorize.md)*
6. Let’s take a look at what it does in our sheet. Leave the script file open and go back to your GSheet tab. Enter your first name in cell A1. Then in cell B1 enter:
```=addCooltoString(A1)```
7. Tab off the cell. This will take your name and add “ is cool” to it.<br /><br />
![Image of step 5](is_cool.png)
8. **Exercise (5-10 min):** Create a function that will take in a whole number and add 2 more than that number to it. *I bet you didn’t know there was going to be Math during this session did you!* So, if we have 5, our new function would be 5 + 7 or 12.

## Final Google Sheet

https://docs.google.com/spreadsheets/d/1wb8yw8zWIOyGSxPgmZvbjonZh9gImeLjYUs7E0ibP_w/edit?usp=sharing
*Don't try to run this script, you'll get an [error](../autherror.png). Copy the code and run it in your own Google Drive.*

## Resource list

Main GAS documentation: https://developers.google.com/apps-script/

Creating custom functions: https://developers.google.com/apps-script/guides/sheets/functions#using_a_custom_function

Bound script: https://developers.google.com/apps-script/guides/bound

## Lessons

[Lesson 1 - Getting Orientated](/Lesson_1/) **(PREVIOUS)**<br />
[Lesson 2 - Create your own function](/Lesson_2/)<br />
[Lesson 3 - Create a custom menu](/Lesson_3/) **(NEXT)**<br />
[Lesson 4 - Sidebar](/Lesson_4/)<br />
[Lesson 5 - Calling APIs](/Lesson_5/)<br />
[Lesson 6 - Scraping the web](/Lesson_6/)<br />
[Lesson 7 - Building a New Book page](/Lesson_7/)<br />
[Lesson 8 - Web App](/Lesson_8/)
