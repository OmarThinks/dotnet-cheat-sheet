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



# 5) See the project Live:


<b>
	

```bash
dotnet watch run
```
</b>


You

