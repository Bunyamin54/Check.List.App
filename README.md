
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

