---
author: Güngör Budak
date: '2013-06-28T18:04:00.000+03:00'
slug: retrieving-data-with-ajax-using-jquery
tags:
- database
- mysql
- pathway
- change
- gene
- biology
- ajax
- jquery
- bind
- protein
- biological databases
- keypress
- php
title: Retrieving Data with AJAX using jQuery, PHP and MySQL
year: '2013'
---

Last semester, I took a course from <a href="http://ii.metu.edu.tr/" target="_blank">Informatics Institute</a> at <a href="http://www.metu.edu.tr/" target="_blank">METU</a> called "<a href="https://catalog.metu.edu.tr/course.php?course_code=9080503" target="_blank">Biological Databases and Data Analysis Tools</a>" where first we learned what is a database and how to do queries on it. Also, the technology behind databases are taught. Then, we learned many biological databases and data analysis tools available. These include gene, protein and pathway databases, tools for creating databases.

As a final project, we were asked to create an online tool that can search a database and get the data and display it on any web browsers. For that, we were given a table and using that table and some given conditions, we retrieved another table from Biomart Ensembl and created the database. Then, in searching and displaying the data, we created a user interface.

<a href="http://www.mysql.com/" target="_blank">MySQL</a> database was used and <a href="http://php.net/" target="_blank">PHP</a> was the choice of programming language, which is powerful and good in web programming.

For our task, we implemented <a href="http://en.wikipedia.org/wiki/Ajax_(programming)" target="_blank">AJAX</a> using <a href="http://jquery.com/" target="_blank">jQuery</a> (a <a href="https://en.wikipedia.org/wiki/JavaScript" target="_blank">JavaScript</a> library). The purpose was to make the search process easy and fast. In this way, the search was triggered when the first three letters from the query were entered and at the same time, the result was displayed on the page without page refresh.

The project is available online on <a href="http://bin503project.byethost18.com/" target="_blank">this website</a>.

To do this, as I said, we used AJAX calls. AJAX works on client-side and provides asynchronous calls from the server without any intervention on the current state on the page. That is, to get the data, we don't have to stop viewing the page and get it, then refresh the page with the data. So, in this way, without page refresh it is possible to get any data from the database.

The method includes the use of jQuery method "<a href="http://api.jquery.com/jQuery.ajax/" target="_blank">ajax</a>". This method gets the necessary information from user, sends it to a scripting language that will work on server such as PHP, and at the end, retrieves the result from the server-side language and shows it to the user.

In the function below, the script gets the value in the text field with id "query" and also the names of check boxes (which determine which column to get from the database) and stores them in an object called "data". Then, when the value of "query" is greater than 2, it executes "ajax" method where submission type is set as "post", the script that weill interact with the database is set as "/process.php", data is given and a callback function which will insert the result into a div with id "results".

```javascript
function getResults() {
  var data = {};
  data['query'] = $("#query").val().trim();
  var boxes = $("input[name=options]:checked"); 
  
  $.each(boxes, function(key, value){
    data[key] = $(value).val();
  });
  
  if (data['query'].length > 2) {
    $.ajax({
      url: '/process.php',
      type: 'post',
      data: data,
      success: function(response) {
        $("#results").html(response);
      }
    });
  }
}
```

And in process.php file, the data coming from AJAX is accepted and used to query the database. Basically, while the data is being retrieved the html codes for the insertion is generated and echoed out at the end. This is how jQuery gets it and displays.

This JavaScript function is able to get the results but it should be somehow executed. There are meny possibilities for this. Typing letters into text field, pasting something into text field, pressing enter, and changing search options are the ones I did. There are great jQuery methods for these, and really simple. We used <a href="http://api.jquery.com/change/" target="_blank">change()</a>, <a href="http://api.jquery.com/bind/" target="_blank">bind()</a>, <a href="http://api.jquery.com/on/" target="_blank">on()</a> and <a href="http://api.jquery.com/keypress/" target="_blank">keypress()</a> methods.

For example, below you can see how ENTER key (the number 13 indicates it) is used to trigger the function. And note that here we prevent the key from submitting form by returning false.

```javascript
$("#query").keypress(function(action) {
  if(action.which == 13) {
    getResults();
    return false;
  }
});
```

The use of others can be found on <a href="http://api.jquery.com/" target="_blank">jQuery documentation</a>.

If you have any question about this post, please leave a comment below.
