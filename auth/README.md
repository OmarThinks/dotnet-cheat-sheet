# 3) Auth




# 1) Create the application with Identity:


<b>

```bash
dotnet new webapp --output "src" --name "Application" --auth Individual
dotnet new mvc --output "src" --name "Application" --auth Individual
dotnet new webapi --output "src" --name "Application" --auth Individual
```
</b>




This application will use SQLite.  
If you want to use SQL Server, just add the **`-uld|--use-local-db`**





```bash
dotnet new webapp --output "src" --name "Application" --auth Individual --use-local-db
dotnet new mvc --output "src" --name "Application" --auth Individual --use-local-db
dotnet new webapi --output "src" --name "Application" --auth Individual --use-local-db
```







---

Change directory to the application directory.
```bash
cd src
```


---

This command will tell bash to trust the self signed
 certificate:

<b>

```bash
dotnet dev-certs https --trust
```
</b>






# 2) Install Requirements :
Before moving on, we need to install requirements:
<b>

```bash
dotnet tool install -g dotnet-aspnet-codegenerator
dotnet tool install --global dotnet-ef
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore
dotnet add package Microsoft.AspNetCore.Identity.UI
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
```
</b>













# 3) Using Custom Identity Model:
This is dangerous, because You will need to use the 
model as a foreign key, and you will need to edit the user.  
So, we create a model called ApplicationUSer, and this is the User.



<b>
Models/ApplicationUser.cs

```cs
using System;
using Microsoft.AspNetCore.Identity;
using SocialApp.Models;
using System.Collections.Generic;

namespace SocialApp.Models
{
    public class ApplicationUser : IdentityUser
    {
        //public List<Post> Posts { get; set; }       
    }
}
```


</b>






```cs
public class ApplicationDbContext : IdentityDbContext 
//Wrong
```
<b>

Make it use the ApplicationUser Model:

```cs
using SocialApp.Models;

public class ApplicationDbContext : IdentityDbContext<ApplicationUser>
//Right
```








In **`Startup.cs`**:



```cs
using SocialApp.Models;

public void ConfigureServices(IServiceCollection services)
{
            services.AddDefaultIdentity<ApplicationUser>(
                options => 
                    {
                        options.Password.RequireDigit = false;
                        options.Password.RequireLowercase = false;
                        options.Password.RequireNonAlphanumeric = false;
                        options.Password.RequireUppercase = false;
                        options.Password.RequiredLength = 6;
                        options.Password.RequiredUniqueChars = 0;
                        options.SignIn.RequireConfirmedEmail = false;
                        options.SignIn.RequireConfirmedAccount = false;
                    })
                .AddEntityFrameworkStores<ApplicationDbContext>();
}
```

</b>






# 5) Migrate:


<b>

```bash
dotnet ef migrations add AuthReady
dotnet ef migrations list
dotnet ef database update 
```
</b>








# 6) Generating (Scaffolding) Identity pages :


<b>

```bash
dotnet aspnet-codegenerator identity
```
</b>

Delete these these:

**Areas/Identity/Data**  
**Areas/Identity/IdentityHostingStartup.cs**


















# 7) Finally: Testing the Application:


<b>

```bash
dotnet watch run
```
</b>





# 7) Testing Auth:


<b>

```bash
dotnet aspnet-codegenerator razorpage "TestingAuth" "Empty" -udl -outDir "Pages"
```



```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.Mvc.RazorPages;

using Microsoft.Extensions.Logging;
using Microsoft.AspNetCore.Authorization;

namespace Application.Pages
{
    [Authorize]
    public class TestingAuthModel : PageModel
    {
        private readonly ILogger<PrivacyModel> _logger;
        public TestingAuthModel(ILogger<PrivacyModel> logger)
        {_logger = logger;}

        public void OnGet()
        {}
    }
}
```
</b>






