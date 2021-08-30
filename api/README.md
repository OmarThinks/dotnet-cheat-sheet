# 5) API





Go to Auth, Continue until Step 7, them come back to me. :)








# 8) Update the launchUrl :


In **`Properties\launchSettings.json`**, update 
**`launchUrl`** from **`swagger`** to **`api/TodoItems`**:


<b>

```json
"launchUrl": "api/TodoItems"
```
</b>





# 9) See the project Live:


<b>
    

```bash
dotnet watch run
```
</b>










# 10) Create a model:

1. Create a new folder called **`Models`**
2. Inside of it, create a new file called **`TodoItem.cs`**
3. Paste this code insde of it

<b>

```csharp
namespace TodoApi.Models
{
    public class TodoItem
    {
        public long TodoItemID { get; set; }
        public string Name { get; set; }
        public bool IsComplete { get; set; }
    }
}
```
</b>











# 11) Generating a controller (Scaffolding) :

We want to create web pages of the Movie model inside the 
pages folder, so we do it like this:

<b>

```bash
dotnet ef dbcontext list

dotnet aspnet-codegenerator controller --controllerName TodoItemsController --model TodoItem --dataContext ApplicationDbContext  -outDir Controllers/api --restWithNoViews
```
</b>







# 12) Migrating:

<b>

```bash
dotnet ef migrations add CreatedTodoItem
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
20210502002257_CreatedTodoItem (Pending)
```



--- 
To perform the migrations:

<b>

```bash
dotnet ef database update
```
</b>





# 13) Finally: Testing the Application:


<b>

```bash
dotnet watch run
```
</b>




