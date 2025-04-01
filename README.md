# DbFirstApproach
DbFirstApproach - Using existing Database do Work

Need this 3 Library
![image](https://github.com/user-attachments/assets/1bb0507b-4a35-458b-a57e-3f3819d4af27)

Step <1> Then Run Command In Nuget Package Console
-> Scaffold-DbContext "Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=janbatchcoreSPMVC;Integrated Security=True" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models

Step <2> from the context FILE THAT IS CREATED INSIDE THE MODEL Folder 
          Example: JanbatchcoreSpmvcContext.cs remove Connection String

Step <3> Then Add the Connection String inside appsettings.json like this 
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "ConnectionStrings": {
    "dbconn": "Data Source=(localdb)\\MSSQLLocalDB;Initial Catalog=janbatchcoreSPMVC;Integrated Security=True"
  },
  "AllowedHosts": "*"
}

Step <4> Define the Builder for Context File using Conn
builder.Services.AddDbContext<JanbatchcoreSpmvcContext>
    (
        options => options.UseSqlServer
        (
            builder.Configuration.GetConnectionString("dbconn")
            )
        );

var app = builder.Build();




