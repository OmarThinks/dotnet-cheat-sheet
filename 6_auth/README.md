# 4) MVC



# 1) Create the application:

<b>

```bash
dotnet new webapi
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
dotnet new webapi --output "1_TodoApi" --name "TodoApi"
```
</b>


---

Change directory to the application directory.
```bash
cd 1_TodoApi
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



Do not forget to double check the **`ToDo.csproj`** file,
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







# 3) Update the launchUrl :


In **`Properties\launchSettings.json`**, update 
**`launchUrl`** from **`swagger`** to **`api/TodoItems`**:


<b>

```json
"launchUrl": "api/TodoItems"
```
</b>





# 4) See the project Live:


<b>
    

```bash
dotnet watch run
```
</b>










# 2) Create a model:

1. Create a new folder called **`Models`**
2. Inside of it, create a new file called **`TodoItem.cs`**
3. Paste this code insde of it

<b>

```csharp
namespace TodoApi.Models
{
    public class TodoItem
    {
        public long Id { get; set; }
        public string Name { get; set; }
        public bool IsComplete { get; set; }
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



Do not forget to double check the **`TodoApi.csproj`** file,
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







# 4) Generating a controller (Scaffolding) :

We want to create web pages of the Movie model inside the 
pages folder, so we do it like this:

<b>

```bash
dotnet aspnet-codegenerator controller --controllerName TodoItemsController --model TodoItem --dataContext TodoContext  -outDir Controllers/api --restWithNoViews
```
</b>









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





# 8) Finally: Testing the Application:


<b>

```bash
dotnet watch run
```
</b>




