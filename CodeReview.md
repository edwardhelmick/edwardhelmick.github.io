## Code Review

##### [Self Assessment](https://edwardhelmick.github.io/index.html) | [Enhancements](https://edwardhelmick.github.io/Enhancements.html)

### Code Review (Pre-Development)
For my project, I am working on three enhancements, software engineering and design, algorithms and data structures, and databases, which together showcase my skills as a developer. I am going to transform a MEAN stack application called Travlr Getaways, which was worked on in my Full Stack Engineering class, to an ASP.NET/C# framework while adding extra features and focusing mainly on administrative interfaces. Below is an analysis of some code which I wish to change, and the reasons why. Generally speaking, all of the issues I find in code here are going to be solved by moving to the ASP.NET framework. The repository of this code review can be found [here]
(https://github.com/edwardhelmick/CS465/settings/access). 

### Enhancement One: Software Engineering and Design

One thing I do not like about the current application is the messy structure of the code. If you look at the file structure, you can see that there are tons of files and a lot of this could be condensed and cleaned up. I personally find the ASP.NET file structure to be much cleaner. Besides my slight dislike of the file structure for MEAN applications, I do believe it will be beneficial for me to learn more about the ASP.NET framework and experience a code merge for such a large application. Developers often have to port applications to different languages and framework for compatibility across devices. A good example of this is an app developer who develops an application on iOS through swift but needs to port it to Java for Android. Having this experience will grant me great exposure to such a task. ASP.NET cleans up the code structure quite a bit but comes with a drawback – it could be less secure since client and server code are mixed within the same file through Razor syntax.  

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
    },
```
More text
    

