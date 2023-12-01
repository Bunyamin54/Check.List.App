
# Demonstration of the app:

   ![Nøsted App Demonstrasjon1](https://github.com/bxn0/ourWinch/assets/112567741/76883913-cd8c-4342-a82c-b3bf321fc848)



<pre>
  ## OurWinch-Nøsted-App (GitHub Repository Root) 

│   ├── ## Root         
│   │   ├── # CSS         
│   │   │   ├── **Layout.css** 
│   │   ├── **Image**         

│   ├── ## Controllers      
│   │   ├── **AccountControllers** 
│   │   ├── **CheckListControllers** 
│   │   ├── **DashboardControllers** 

│   ├── ##Data              
│   │   ├── **AppDbContext**   

│   ├── ##Migrations        

│   ├── ##Models        
│   │   ├── **AccountModel**  
│   │   ├── **ChecklistModel**
│   │   ├── **DashboardModel**
│   │   ├── **ErrorViewModel**

│   ├── ##Services         

│   ├── ##Views           
│   │   ├── **Account**       
│   │   ├── **Dashboard**     
│   │   ├── **Electro**       
│   │   ├── **FunksjonsTest** 
│   │   ├── **Hydrolisk**     
│   │   ├── **Mechanical**
│   │   ├── **Roles**         
│   │   ├── **ServiceOrder**  
│   │   ├── **ServiceSkjema** 
│   │   ├── **Trykk**         

│   ├── ##Shared         
│   │   ├── **Layout.cshtml** 
│   │   ├── **appsettings.json**

│   ├── ##DockerFile         

│   ├── ##Program.cs
</pre>


This code block follows the MVC (Model-View-Controller) architectural pattern. This pattern separates the application into three main components, providing a modular and easily maintainable structure.

## * Model

Includes data models such as the AppDbContext class and Identity-related classes (ApplicationUser, IdentityRole, etc.). Database operations and user authorization processes are handled in this layer.
 <pre> 
 ## Models 

  │   ├── **AccountModel**        
  │   ├── **ChecklistModel**      
  │   ├── **DashboardModel**      
  │   ├── **ErrorViewModel**      

</pre>

## * View

Includes elements related to the user interface, such as Razor pages in the Views folder and static files (CSS, JavaScript, etc.) in the wwww root folder.
 <pre>
 ## Views 

  │   ├── **Account**          
  │   ├── **Dashboard**        
  │   ├── **Electro**         
  │   ├── **FunksjonsTest**   
  │   ├── **Hydrolisk**       
  │   ├── **Mechanical**      
  │   ├── **Roles**           
  │   ├── **ServiceOrder**    
  │   ├── **ServiceSkjema**   
  │   ├── **Trykk**  
  │   ├── **User**          

      </pre>    


## * Controller

Controller classes like AccountController receive HTTP requests, initiate processes, and redirect to the appropriate view to display results.
 <pre>
## Controllers

   │   ├── **AccountControllers**    
   │   ├── **CheckListControllers** 
   │   ├── **DashboardControllers** 

</pre>


## Docker Compose Configuration

### Version
- `version: '3.4'`  
  Specifies the Docker Compose file format version. Compatible with Docker Engine 17.09.0+.

### Services
This section defines two services: `app` and `db`.

#### App Service
- `image: app-image`  
  The Docker image for the application is named `app-image`. Docker will pull it from a registry if it's not found locally.
- `build`:
  - `context: .`  
    The build context is set to the current directory.
  - `dockerfile: Dockerfile`  
    Specifies the Dockerfile in the current directory for building the image.
- `ports`:
  - `"80:5002"` and `"443:5002"`  
    Maps port 5002 inside the container to ports 80 and 443 on the host machine, likely for HTTP and HTTPS traffic.
- `environment`:
  - Sets environment variables like `ASPNETCORE_ENVIRONMENT` and the database connection string (`ConnectionStrings__DefaultConnection`).
- `depends_on`:
  - Indicates a dependency on the `db` service. Docker Compose will start `db` first.

#### DB Service
- `image: mcr.microsoft.com/mssql/server`  
  Uses the official Microsoft SQL Server image.
- `environment`:
  - Sets the SA password and accepts the EULA.
- `ports`:
  - Maps port 1433 inside the container to port 1433 on the host machine.
- `volumes`:
  - Uses a volume named `dbdata` to persist data.

### Volumes
- `dbdata`:  
  A named volume for the database service, where SQL Server stores its data files.




![2023-11-27_14-43-19](https://github.com/bxn0/ourWinch/assets/82652466/1b96c4d9-195e-4f80-97ec-cfd03d3e190b)


### User Registiration & Authentication
User registration and editing can only be done by administrators. Administrators can add, delete, or edit new administrators and mechanics in the system. Registered users can securely log into the system, see the interface according to their roles, and perform operations.

### Dashboard Operations
- The admin can access the customer reports pages, along with other pages, and can view and edit the information there.
- Users can see active and completed service orders.
- Users can create new service requests.
- Mechanics can access checklist pages through active service orders and can safely perform their checks and save them along with their own comments.
- For orders with completed checks, the service schema can be accessed again through the active service page, and the results of the service can be viewed here. The output of this page can be printed and sent to the customer along with some recommendations, providing information on the changes made and those that are recommended.


## Identity Service

The Identity service added with the AddIdentity method handles user management and authorization processes, including operations like user registration, login, and role management.

## Migration for Adding Identity Tables

This migration script adds the necessary tables for ASP.NET Core Identity. It includes tables for roles, users, role claims, user claims, user logins, user roles, and user tokens.

## Tables Created

- `AspNetRoles`: Stores roles information.
- `AspNetUsers`: Stores users information.
- `AspNetRoleClaims`: Stores role claims.
- `AspNetUserClaims`: Stores user claims.
- `AspNetUserLogins`: Stores user logins.
- `AspNetUserRoles`: Stores user roles.
- `AspNetUserTokens`: Stores user tokens.

## How to Apply the Migration

To apply this migration, run the following command in the Package Manager Console:

bash - Update-Database

## How to Rollback the Migration

If needed, you can rollback the migration by running the following command:

### Remove-Migration

# Database Connection

Entity Framework Core, added with the AddDbContext method on AppDbContext, manages database operations. Access, query, and update operations on the database are performed through this layer.

using Microsoft.AspNetCore.Identity.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore;


/// <summary>
/// Represents the database context for the application, derived from IdentityDbContext for user management.
/// </summary>
public class AppDbContext : IdentityDbContext<ApplicationUser>
{
    /// <summary>
    /// Initializes a new instance of the <see cref="AppDbContext"/> class.
    /// </summary>
    /// <param name="options">The options to be used by the context.</param>
    public AppDbContext(DbContextOptions<AppDbContext> options) : base(options)
    {
        // Constructor logic.
    }

    /// <summary>
    /// Gets or sets the DbSet for ServiceOrders.
    /// </summary>
    public DbSet<ServiceOrder> ServiceOrders { get; set; }

   

    /// <summary>
    /// Gets or sets the DbSet for ApplicationUser.
    /// </summary>
    public DbSet<ApplicationUser> ApplicationUser { get; set; }
}

## Swagger and Notyf Service

Swagger is used to generate and view API documentation (AddSwaggerGen, UseSwagger, UseSwaggerUI). The Notyf service is used for managing notifications (AddNotyf).

## Email Sending Service

The MailJetEmailSender class is used to perform email sending operations. This class implements the IEmailSender interface.

## ServiceSkjemaService

The ServiceSkjemaService class represents a custom service, likely performing tasks such as business logic, data processing, or interaction with another service. This service is added with the AddScoped method, creating a scope for each HTTP request.

Interactions between these main components occur through HTTP requests and are handled by controllers. Controllers execute business logic, call services if necessary, and redirect results to views. This modular structure allows each component to have clear responsibilities.

