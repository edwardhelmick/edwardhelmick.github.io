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

Example of LINQ being used to find an object where the object id is the id being searched for in this application:
```
TripDetails tripDetails = collection.Where(c => c.Id == id).FirstOrDefault();
```

### Enhancement Three: Databases

During the final section of my project enhancements, which focused on database implementation and improvement, I decided to work through getting a hosted cluster running on the MongoDB website. I am using a free student version which is very limited but was sufficient for this project. As mentioned above, I spent a lot of time working with MongoDB and understanding how the drivers worked – which also meant understanding how to configure the cluster, create a new table, and add information to it programmatically. It was quite a fun experience! In addition to setting up this hosted cluster, I implemented some more advance database querying. As an example, I implemented an asynchronous update method, which uses the Builders MongoDB driver class – a static helper class which does various things. In this case, it is building the new object to replace the old one, therefore updating the information in the object.

```
var update = collection.FindOneAndUpdateAsync(Builders<TripDetails>.Filter.Eq("Id", trip.Id), Builders<TripDetails>.Update
                    .Set("Code", trip.Code)
                    .Set("Name", trip.Name)                    
                    .Set("LengthDays", trip.LengthDays)
                    .Set("StartDate", trip.StartDate)
                    .Set("ResortName", trip.ResortName)
                    .Set("CostPerPerson", trip.CostPerPerson)
                    .Set("Img_Base64", trip.Img_Base64)
                    .Set("Description", trip.Description));
```
Another interesting thing that I have done is used a string field labeled Img_Base64 to store the base64 image string that a user uploads to the application. This is a good way to manage image storage on a database, and is quick to convert back to an image for showing on a page, as seen below.

```
string img = item.Img_Base64;
if (!String.IsNullOrEmpty(img)) {
 <img src="data:image/png;base64, @img" style="height: 200px; width: 200px;" />
}
```


