## Code Review

##### [Self Assessment](https://edwardhelmick.github.io/index.html) | [Enhancements](https://edwardhelmick.github.io/Enhancements.html)

### Code Review (Pre-Development)
For my project, I am working on three enhancements, software engineering and design, algorithms and data structures, and databases, which together showcase my skills as a developer. I am going to transform a MEAN stack application called Travlr Getaways, which was worked on in my Full Stack Engineering class, to an ASP.NET/C# framework while adding extra features and focusing mainly on administrative interfaces. Below is an analysis of some code which I wish to change, and the reasons why. Generally speaking, all of the issues I find in code here are going to be solved by moving to the ASP.NET framework. The repository of this code review can be found [here]
(https://github.com/edwardhelmick/CS465/settings/access). 

### Enhancement One: Software Engineering and Design

One thing I do not like about the current application is the messy structure of the code. If you look at the file structure, you can see that there are tons of files and a lot of this could be condensed and cleaned up. I personally find the ASP.NET file structure to be much cleaner. Besides my slight dislike of the file structure for MEAN applications, I do believe it will be beneficial for me to learn more about the ASP.NET framework and experience a code merge for such a large application. Developers often have to port applications to different languages and framework for compatibility across devices. A good example of this is an app developer who develops an application on iOS through swift but needs to port it to Java for Android. Having this experience will grant me great exposure to such a task. ASP.NET cleans up the code structure quite a bit but comes with a drawback – it could be less secure since client and server code are mixed within the same file through Razor syntax. Below is some code showing an example of how the application is using JavaScript to define routers and initalize application variables:

```
require('dotenv').config();

var createError = require('http-errors');
var express = require('express');
var path = require('path');
var cookieParser = require('cookie-parser');
var logger = require('morgan');
var hbs = require('hbs');
const passport = require('passport');

require('./app_api/models/db');
require('./app_api/config/passport');

var indexRouter = require('./app_server/routes/index');
var usersRouter = require('./app_server/routes/users');
var travelRouter = require('./app_server/routes/travel');
const apiRouter = require('./app_api/routes/index')

var app = express();

// view engine setup
app.set('views', path.join(__dirname, 'app_server', 'views'));

// register handlebars partials (https://www.npmjs.com/package/hbs)
hbs.registerPartials(path.join(__dirname, 'app_server', 'views/partials'));

app.set('view engine', 'hbs');

app.use(logger('dev'));
app.use(express.json());
app.use(express.urlencoded({ extended: false }));
app.use(cookieParser());
app.use(express.static(path.join(__dirname, 'public')));
app.use(passport.initialize());

//allow CORS
app.use('/api', (req, res, next) => {
  res.header('Access-Control-Allow-Origin', 'http://localhost:4200');
  res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept, Authorization');
  res.header('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE');
  next();
});

app.use('/', indexRouter);
app.use('/users', usersRouter);
app.use('/travel', travelRouter);
app.use('/api', apiRouter);

//catch unauthorized error and create 401
app.use((err, req, res, next) => {
  if (err.name === 'UnauthorizedError') {
    res
      .status(401)
      .json({"message": err.name + ": " + err.message});
  }
});

// catch 404 and forward to error handler
app.use(function(req, res, next) {
  next(createError(404));
});

// error handler
app.use(function(err, req, res, next) {
  // set locals, only providing error in development
  res.locals.message = err.message;
  res.locals.error = req.app.get('env') === 'development' ? err : {};

  // render the error page
  res.status(err.status || 500);
  res.render('error');
});

module.exports = app;
```
Migrating these specific bits of code to the ASP.NET framework will likely prove to be the most challenging part of the entire project. 

### Enhancement Two: Algorithms and Data Structures

This application does not use any specific algorithm and uses JSON data structures since it uses MongoDB. My plan to improve this area of the application is to use LINQ (Language Integrated Query). It is a very powerful feature of C# which allows developers to quickly aggregate and manipulate data sets. Another thing I plan on doing is modifying the object model to use a base64 image string and convert it in the browser. This will allow for an easy way to store images in the database instead of in the file system.
### Enhancement Three: Databases

The application uses a local database to store information. This means that if the application were deployed on the web to users, it would have to be taken down for each update. Instead, I will be setting up a MongoDB cluster hosted on the MongoDB site. This will allow for the application to be updated with data seamlessly and without system interruptions. For example, see the code snippet below:
```
    "1": {
        "code": "GALR210214",
        "name": "Gale Reef",
        "length": "4 nights / 5 days",
        "start": "2021-02-14T08:00:00Z",
        "resort": "Emerald Bay, 3 stars",
        "perPerson": "799.00",
        "image": "reef1.jpg",
        "description": "<p>...</p>"
    }
```
This is how the model is implemented in the current application. It is stored locally in a .JSON file. I plan on saving these JSON models to the database, and then use the MongoDB driver to retrieve them from the database, use LINQ to aggregate them and select them as necessary, and display them to the user on the view. LINQ is a nice addition to this and learning it will prove useful for me in the future. It is a highly productive tool and reduces developer error while improving efficiency. 
    

