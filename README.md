# Dummy Credentials for login 
# For Admin:
## mobil: [94719352]  pass: [Icardi1990!]
# For Ansatt:
## mobil: [94717177]  pass: [Icardi1990!]

# Demonstration of the app:
![IGLAND WINCH]![My-Movie-2-2](https://github.com/bxn0/ourWinch/assets/60920330/1b61cd29-58e9-475f-9295-c3993a5faee2)



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
