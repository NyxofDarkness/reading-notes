# Read: 11 - EJS

## Watch EJS tutorial from WalkThroughCode on YouTube, Videos 1-5
> Note that this series of videos should take approximately 20 minutes to watch

> Ability to inject a variable using express inside of a route
> loop over an array of values, commonly json
> if else statements like adding or editing a form
> Layout file i.e. mustache
 
 Flow: 
 ```
 npm init -y
 ```
 fills everything out
 ```
 npm install --save express body-parser cors ejs
 ```
 ```
 var express = require('express');
 var bodyParser = require('bodyParser');
 var cors = require('cors);
 var path = require('path');

 var app = express();

 app.use(bodyParser());
 app.use(cores());

 app.set('views', path.join(__dirname, 'views'));
 app.set('view engine', 'ejs');

 app.get('/', function(request, response) {
   response.render('index');
 });

app.listen(8000, function() {
  console.log('heard on 8000');
})
 ```
 > path joins two together. it concatinates them

 > need index.ejs file

## injecting value and evaluate

>

Skim: EJS Tutorial
Skim: Source Code for the EJS Tutorial
Review the code that goes along with the tutorial