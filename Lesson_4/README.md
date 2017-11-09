# Lesson 4 - Sidebar

In this lesson we'll create a custom input window (sidebar) in a Google Doc.

## Lesson Steps

1. Open Google Drive: https://drive.google.com
2. Create a new Google Doc and name our file: "LITA 2017 Custom Sidebar (Lesson 4)"
3. Click on Tools menu and choose Script Editor. 
4. Copy in this code overwriting everything that is there:
```javascript
function showSidebarWindow() {
  var ui = DocumentApp.getUi();
  var html = HtmlService.createTemplateFromFile('sidebar').evaluate()
             .setTitle('Sidebar Example').setWidth(300)
             .setSandboxMode(HtmlService.SandboxMode.NATIVE);
  ui.showSidebar(html);
}
```
5. Save and name your script. This code, when called, will open the sidebar file and make it appear as a sidebar in our Google Doc. 
6. Let's create our sidebar file. In the Script editor, click File -> New -> Html file to create a blank template for our sidebar. 
7. Copy in this code overwriting everything that is there:
```
Hello, world! <input type="button" value="Close" onclick="google.script.host.close()" />
```
8. Save and name your file 'sidebar'.
9. **Excersize (5 min):** How might we call this function when a user opens this Doc? Implement this code, save, close your file and test that opening the Doc shows the sidebar.

## Final Google Sheet

https://docs.google.com/document/d/1IyrinPgOSSnMaBgHfOkfuJPt_FG5Cd-QqNTP7qj_E6k/edit?usp=sharing

## Resource list

Main GAS documentation: https://developers.google.com/apps-script/

Dialogs and Sidebars: https://developers.google.com/apps-script/guides/dialogs

Class Ui: https://developers.google.com/apps-script/reference/base/ui

