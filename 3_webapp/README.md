# 3) Web Application:



# 1) Create the application:

<b>

```bash
dotnet new webapp
```
</b>

This has a list of parameters that can be used with it:


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
dotnet new webapp --output "1_hello_app" --name  "hello_app"
```
</b>



---

This command will tell bash to trust the self signed
 certificate:

<b>

```bash
dotnet dev-certs https --trust
```
</b>
# 2) Create a model:

1. Create a new folder called **`Models`**
2. Inside of it, create a new file called **`Movie.cs`**
3. Paste this code insde of it

<b>

```csharp
using System;
using System.ComponentModel.DataAnnotations;

namespace RazorPagesMovie.Models
{
    public class Movie
    {
        public int ID { get; set; }
        public string Title { get; set; }

        [DataType(DataType.Date)]
        public DateTime ReleaseDate { get; set; }
        public string Genre { get; set; }
        public decimal Price { get; set; }
    }
}
```
</b>









# 3) Code Generation (Scaffolding) Requirements :
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







# 4) Code Generation (Scaffolding) :

We want to create web pages of the Movie model inside the 
pages folder, so we do it like this:

<b>

```bash
dotnet aspnet-codegenerator razorpage --model Movie --dataContext AppDataContext -outDir Pages/Movies -udl -scripts
```
</b>


- **`--model`**
	- The moidel that will be relted to the pages
	- Here we used the model **`Movie`** that we have just created
- **`--dataContext`**
	- The database
	- here we have created a database called **`AppDataContext`**
- **`-outDir`**
	- This code created a folder called **`Movies`** inside the pages directory
- **`-udl`**
	- Use Default Layout
	- If do not specify a layout, it will be plain HTML
	- Default layout is a Bootstrap layout
- **`-scripts`**
	- To use JavaScript



- Files **Updated**:
	- **` appsettings.json`**
		- String to connect to the local database
- Files **Created**:
	- **`Pages/Movies:`**
		- Create, update, delete and list files
	- **`Data/AppDataContext.cs`**
		- Updated the database


# 5) See the project Live:


<b>
	

```bash
dotnet watch run
```
</b>


Check these links:

**https://localhost:5001  
https://localhost:5001/Movies/create**





# 6) Install Entity Framework Globally:

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






# 7) Migrating:

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










