# 4) Web Application:




Go to Auth, Continue until Step 7, them come back to me. :)



# 8) Create a model:

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
        public int MovieID { get; set; }
        public string Title { get; set; }

        [DataType(DataType.Date)]
        public DateTime ReleaseDate { get; set; }
        public string Genre { get; set; }
        public decimal Price { get; set; }
    }
}
```
</b>







# 9) Code Generation (Scaffolding) :

We want to create web pages of the Movie model inside the 
pages folder, so we do it like this:

<b>

```bash
dotnet ef dbcontext list

dotnet aspnet-codegenerator razorpage --model Movie --dataContext ApplicationDataContext -outDir Pages/Movies -udl -scripts
```
</b>


- **`--model`**
	- The moidel that will be relted to the pages
	- Here we used the model **`Movie`** that we have just created
- **`--dataContext`**
	- The database
	- here we have created a database called **`ApplicationDataContext`**
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


# 10) See the project Live:


<b>
	

```bash
dotnet watch run
```
</b>


Check these links:

**https://localhost:5001  
https://localhost:5001/Movies/create**






# 11) Migrating:

<b>

```bash
dotnet ef migrations add MovieCreated
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
20210502002257_MovieCreated (Pending)
```



--- 
To perform the migrations:

<b>

```bash
dotnet ef database update
```
</b>





# 12) Finally: Testing the Application:


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


