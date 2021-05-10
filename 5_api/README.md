# 4) MVC



# 1) Create the application:

<b>

```bash
dotnet new mvc
```
</b>

This has a list of important parameters that can be used with it:


- **`--output`**:
    - Specify the location to put the project
- **`--name`**:
    - The name of the project
- **`--auth`**:
    - The Authentication system of the project
- **`--no-https`**:
    - To create the project without https

So, we will use this command to create the application:



<b>

```bash
dotnet new mvc --output "2_MvcMovie" --name "MvcMovie"
```
</b>


---

Change directory to the application directory.
```bash
cd 2_MvcMovie
```


---

This command will tell bash to trust the self signed
 certificate:

<b>

```bash
dotnet dev-certs https --trust
```
</b>




<b>
    

```bash
dotnet watch run
```
</b>








# 2) Code Generation (Scaffolding) Requirements :
Before we can apply scaffolding, we need to install some packages:

<b>

```bash
dotnet tool install -g dotnet-aspnet-codegenerator
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```
</b>



Do not forget to double check the **`hello_app.csproj`** file,
you should see these codes:

<b>

```xml
<ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="5.0.5">
        <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
        <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="5.0.5" />
    <PackageReference Include="Microsoft.VisualStudio.Web.CodeGeneration.Design" Version="5.0.2" />
</ItemGroup>
```
</b>

Now we are ready to start code generation.







# 3) Generating an Empty Controller :


<b>

```bash
dotnet aspnet-codegenerator controller --controllerName HelloWorldController -outDir Controllers -udl -scripts --noViews
```
</b>











# 4) See the project Live:


<b>
    

```bash
dotnet watch run
```
</b>


Check these links:

**https://localhost:5001  
https://localhost:5001/Movies/create**











# 5) Generating an Empty Razor View :



<b>

```bash
dotnet aspnet-codegenerator view Index Empty -outDir Views/HelloWorld -udl -scripts
```
</b>







# 6) Create a model:

1. Create a new folder called **`Models`**
2. Inside of it, create a new file called **`Movie.cs`**
3. Paste this code insde of it

<b>

```csharp
using System;
using System.ComponentModel.DataAnnotations;

namespace MvcMovie.Models
{
    public class Movie
    {
        public int Id { get; set; }
        public string Title { get; set; }

        [DataType(DataType.Date)]
        public DateTime ReleaseDate { get; set; }
        public string Genre { get; set; }
        public decimal Price { get; set; }
    }
}
```
</b>













# 7) Creating Controllers With Views (Scaffolding) :

We want to create controllers of the Movie model inside the 
Controllers folder, so we do it like this:

<b>

```bash
dotnet aspnet-codegenerator controller --controllerName MoviesController -outDir Controllers --model Movie --dataContext MvcMovieContext -udl -scripts
```
</b>



Generated files:



```
Added DbContext : '\Data\MvcMovieContext.cs'
Added Controller : '\Controllers\MovieController.cs'.
Added View : \Views\Movie\Create.cshtml
Added View : \Views\Movie\Edit.cshtml
Added View : \Views\Movie\Details.cshtml
Added View : \Views\Movie\Delete.cshtml
Added View : \Views\Movie\Index.cshtml
```











































































# 7) Install Entity Framework Globally:

<b>

```bash
dotnet tool install --global dotnet-ef
```
</b>

To make sure that the package has been successfull 
installed globally, type thsi command:


<b>

```bash
dotnet ef --help
```
</b>

You should see now list of ef commands.






# 8) Migrating:

<b>

```bash
dotnet ef migrations add InitialCreate
```
</b>
This will prepare the files for migrating the databse.

---

Files changed:

Now you can see a migrations folder created, 
and the migrations, are in it.

---

<b>

```bash
dotnet ef migrations list
```
</b>

To see a list of migrations until now.

The result should look like this:

```
20210502002257_InitialCreate (Pending)
```



--- 
To perform the migrations:

<b>

```bash
dotnet ef database update
```
</b>





# 9) Finally: Testing the Application:


<b>

```bash
dotnet watch run
```
</b>


Test these links:

<b>

https://localhost:5001/  
https://localhost:5001/Movies  
https://localhost:5001/Movies/create    

</b>
Try adding, deleting and editing the database 
from the frontend.


