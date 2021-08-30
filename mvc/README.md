# 5) MVC





Go to Auth, Continue until Step 7, them come back to me. :)




# 8) Generating an Empty Controller :


<b>

```bash
dotnet aspnet-codegenerator controller --controllerName HelloWorldController -outDir Controllers -udl -scripts --noViews
```
</b>











# 9) See the project Live:


<b>
    

```bash
dotnet watch run
```
</b>


Check these links:

**https://localhost:5001  
https://localhost:5001/Movies/create**











# 10) Generating an Empty Razor View :



<b>

```bash
dotnet aspnet-codegenerator view Index Empty -outDir Views/HelloWorld -udl -scripts
```
</b>







# 11) Create a model:

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













# 12) Creating Controllers With Views (Scaffolding) :

We want to create controllers of the Movie model inside the 
Controllers folder, so we do it like this:

<b>

```bash
dotnet ef dbcontext list

dotnet aspnet-codegenerator controller --controllerName MoviesController -outDir Controllers --model Movie --dataContext ApplicationDbContext -udl -scripts
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




























































# 13) Migrating:

<b>

```bash
dotnet ef migrations add CreatedMovie
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
20210502002257_CreatedMovie (Pending)
```



--- 
To perform the migrations:

<b>

```bash
dotnet ef database update
```
</b>





# 14) Finally: Testing the Application:


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


