# 6) Auth



# 1) Create the application:


<b>

```bash
dotnet new webapp --output "WebApp1" --name "WebApp1" --auth Individual
```
</b>


---

Change directory to the application directory.
```bash
cd WebApp1
```


---

This command will tell bash to trust the self signed
 certificate:

<b>

```bash
dotnet dev-certs https --trust
```
</b>






# 3) Code Generation (Scaffolding) Requirements :
Before we can apply scaffolding, we need to install some packages:

<b>

```bash
dotnet tool install -g dotnet-aspnet-codegenerator
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore
dotnet add package Microsoft.AspNetCore.Identity.UI
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
```
</b>


Now we are ready to start code generation.




# 4) Install Entity Framework Globally:

<b>

```bash
dotnet tool install --global dotnet-ef
```
</b>

To make sure that the package has been successfull 
installed globally, type thsi command:








# 4) Generating (Scaffolding) Identity pages :


<b>

```bash
dotnet aspnet-codegenerator identity
```
</b>

Delete these these:

**Areas/Identity/Data**  
**Areas/Identity/IdentityHostingStartup.cs**







# 5) Not Requiring email Confirmation :

In **`Startup.cs`**

<b>

```cs
public void ConfigureServices(IServiceCollection services)
{
    services.AddDefaultIdentity<IdentityUser>(options => {
                options.SignIn.RequireConfirmedAccount = false;
            }
        )
        .AddEntityFrameworkStores<ApplicationDbContext>();
}
```
</b>










# 8) Finally: Testing the Application:


<b>

```bash
dotnet watch run
```
</b>




