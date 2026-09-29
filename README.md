# Bellbloom
A school management system with built-in authentication. It is used to handle academic data conveniently for both students and teachers.  

## Prerequisites
1. .NET 8 SDK
2. PostgreSQL


*Note: Tables are set up on application startup.*

## Setup
1. Clone the repository.
2. Copy appsettings.Example.json to appsettings.json
3. Set your database connection string under “ConnectionStrings” and JWT key under “JWTConfig”.
4. Run the application with `dotnet run`.  
**JWTConfig key must be at least 32 characters at startup.** 

## Once Running
Endpoints are viewable from your local machine at https://localhost:port/swagger

Refer to the [documentation](Bellbloom%20API%20Reference.md) for how to sign up, log in, and authorize in Swagger.


## Troubleshooting
**Q:** *The application crashes on launch with a connection error. Why?*\
**A:** *Double check that your server is running and that your connection string is correct. Missing either of these will prevent the application from running.*

**Q:** *Tables and databases were not created. Why?*\
**A:** *The database user needs permissions to create databases and tables. Use a superuser such as postgres locally, or create an empty SchoolManagement database first.* 

**Q:** *Why isn’t my Swagger page loading?*\
**A:** *Swagger only runs when the environment is Development. Run with `dotnet run` or set as the default environment with `ASPNETCORE_ENVIRONMENT=Development`*

**Q:** *The browser warns about the HTTPS certificate.* \
**A:** *Run `dotnet dev-certs https --trust` once.*

**Q:** *Why does every request return 401 even after logging in?*\
**A:** *You have inputted the token incorrectly, or it expired.*


## Built with
.NET 8\
ASP.NET Core Web API\
EF Core\
PostGreSQL\
JWT

