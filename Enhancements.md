## Enhancements

##### [Self Assessment](https://edwardhelmick.github.io/index.html)  |  [Code Review](https://edwardhelmick.github.io/CodeReview.html)

For my computer science capstone at Southern New Hampshire University, I chose one artifact to focus on enhancing throughout the entire course. The artifact I chose to enhance is Travlr Getaways – a web application on the MEAN stack (MongoDB, ExpressJS, AngularJS, and Node) which was worked on in my previous Full Stack Engineering class. This artifact was a great choice for this enhancement project because it is a large application with endless opportunities for creative change and improvements. I learned a lot while transforming this application and enjoyed the experience.

### Enhancement One: Software Design and Engineering

I decided to transform this application from a MEAN stack application to an ASP.NET application. They are very similar, but ASP.NET has a lot of great built in security functions and this application could easily be expanded in the future to include user accounts and role management. Transferring this application to a different language and web framework was a great learning experience for me. I spent time understanding how the MongoDB drivers worked differently on C#.

Code to initialize the database object from Mongo:

```
string constr = ConfigurationManager.AppSettings["connectionString"];
MongoClient Client = new MongoClient(constr);
IMongoDatabase DB = Client.GetDatabase("Trips");
```

Connection string from the Web.config XML file:

```
<appSettings>
      <add key="connectionString" value="mongodb+srv://ehelmick93:redacted@cluster0.cmv2d.mongodb.net/Testdatabase?retryWrites=true&amp;w=majority" />
</appSettings>
```

Additionally, I spent a lot of time learning how models were initialized differently between languages and how to configure connection strings on the new framework. I would say the most difficult part was working through connecting my database server to the newly built application, but it was very rewarding when accomplished! The migration to a different language and framework showcases my ability to adapt quickly to change, analyze how to execute the required changes in the new environment, and learn new technologies.

### Enhancement Two: Algorithms and Data Structures

During this section of my project enhancement, I decided to add in LINQ. LINQ stands for language integrated query. It is a powerful tool in C# which allows you to aggregate and manipulate data sets efficiently. I thought it would be useful to spend some time learning and using LINQ in this project since it is widely used in ASP.NET applications throughout the industry. Using LINQ, I was able to aggregate all of the trips from the database and send them to the trips view for user interaction. I also used LINQ to find specific records by ID in the list of trips to delete and update records. The integration of LINQ to this project has increased efficiency and would allow for the application to scale significantly had it been a real-life production application.
### Enhancement Three: Databases

What did I achieve with this enhancement?
What did I learn?

