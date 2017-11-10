# Lesson 8 - Web App

In this lesson we'll create a new Google Apps Script Web App.

## Lesson Steps

In the previous lesson, we built a New Book page. It was nice and functional, but requires us to update our display HTML file every time we add new data. With GAS Web Apps we can create a script that will dynamically include content in a webpage instead.

1. Open Google Drive: https://drive.google.com
2. **Copy** your Google Sheet from [Lesson 7](../Lesson_7/). If you didn't have time to finish, copy the final version listed at the bottom. Name it: "LITA 2017 New Book List Web App (Lesson 8)".
3. Click on the Tools menu and choose Script Editor.<br /> 
4. Add this code to your existing code.
```javascript
function doGet() {
  var html = HtmlService.createTemplateFromFile('books').evaluate()
            .setTitle('web app').setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL);
  return html;
}
```
5. The doGet() function is a special function that tells the script how to serve the content to who ever calls our Web App. The function creates a template from the 'books' file. Then sends it back to the application that called it.
6. Let's create our 'books' File. Click File -> New -> Html file and replace the existing code with this:
```
<!DOCTYPE html>
<html>
  <head>
    <base target="_top">  <!-- Compiled and minified CSS -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.100.2/css/materialize.min.css">

  </head>
  <body>
    <div class="container">
    <div id="books">

<!-- class="search" automagically makes an input a search field. -->
  <input class="search" placeholder="Search" />
<!-- class="sort" automagically makes an element a sort buttons. The date-sort value decides what to sort by. -->
  <button class="sort" data-sort="title">
    Sort
  </button>

<!-- Child elements of container with class="list" becomes list items -->
  <ul class="list">
    <li><img width='10%' src='https://fakecatalog.files.wordpress.com/2017/11/book1.png' /><a class='title' href='https://fakecatalog.wordpress.com/abc321465498/'> The Big Book of Number 1s</a> by Zeus</li>
<li><img width='10%' src='https://fakecatalog.files.wordpress.com/2017/11/book2.png' /><a class='title' href='https://fakecatalog.wordpress.com/hij18842f532/'> The Big Book of Stars</a> by Apollo</li>
<li><img width='10%' src='https://fakecatalog.files.wordpress.com/2017/11/book31.png' /><a class='title' href='https://fakecatalog.wordpress.com/lmn458137952/'> The Big Book of Long Ovals</a> by Athena</li>
<li><img width='10%' src='https://fakecatalog.files.wordpress.com/2017/11/book4.png' /><a class='title' href='https://fakecatalog.wordpress.com/mno545558501/'> The Big Book Vertical Ovals</a> by Demeter</li>
<li><img width='10%' src='https://fakecatalog.files.wordpress.com/2017/11/book5.png' /><a class='title' href='https://fakecatalog.wordpress.com/rst824713975/'> The Big Book of Rectangles</a> by Poseidon</li>
<li><img width='10%' src='https://fakecatalog.files.wordpress.com/2017/11/book6.png' /><a class='title' href='https://fakecatalog.wordpress.com/xyz582528202/'> The Big Book of Polygons</a> by Hera</li>
    
  </ul>
</div>
    
  <script src="https://cdnjs.cloudflare.com/ajax/libs/list.js/1.5.0/list.min.js"></script>
  <script>
  
  var options = {
  valueNames: [ 'title' ]
};

var userList = new List('books', options);

</script>
</div>
  </body>
</html>
```
7. Save your files. *[Remember you may have to authorize your script.](../authorize.md)* 
8. Now click on the Publish -> Deploy as web app menu.<br /><br /> 
![Image of publish screen](publish.png)
9. See Google's help for [details about each setting](https://developers.google.com/apps-script/guides/web#deploying_a_script_as_a_web_app), but most remain at their defaults. Typically, you should create a new version each time you publish to ensure your Web App gets updated.
10. Now we can open the apps URL.<br /><br />
![Image of web app](web_app.png)
11. Copy the URL and paste it into a new browser window<br /><br />
![Image of web app new book](web_app_new_book.png)<br />
12. You can also use an iframe tag to embed the Web App in a web page
```
<iframe frameborder="0" src="https://script.google.com/a/meyerhofer.com/macros/s/AKfycbxNtxCOK_NB_BKGiPL9GXlpUNzmyFS2XhCFObLVtqv3_Jgzdto/exec" style="width: 625px; height: 800px;"></iframe>
```
Or in a LibGuide:
![Image of web app libguide](libguide.png)
13. **Exercise (5 min):** Add another row of data and re-publish your app. Did you see it represented in your webpage or LibGuide?
<br /><br />
*Interested in pushing Google Apps Script even further? Check out [HTML Service: Communicate with Server Functions](https://developers.google.com/apps-script/guides/html/communication) to learn about communicating between webpages, your user, and Google Apps Script.*

## Final Google Sheet

https://docs.google.com/spreadsheets/d/1ilFmn1fQ_ZvCcYV2tifZNOgSslbfGvHgzvxhkDXEw0A/edit?usp=sharing
*Don't try to run this script, you'll get an [error](../autherror.png). Copy the code and run it in your own Google Drive.*

## Resource list 

Main GAS documentation: https://developers.google.com/apps-script/

Web Apps: https://developers.google.com/apps-script/guides/web

HTML Service: https://developers.google.com/apps-script/guides/html/
