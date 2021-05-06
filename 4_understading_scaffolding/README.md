# 4) Understading Scaffolding:


# 1) Looking at the code:


<b>

Pages/Movies/Index.cshtml.cs
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.Mvc.RazorPages;
using Microsoft.EntityFrameworkCore;
using RazorPagesMovie.Models;

namespace hello_app.Pages_Movies
{
    public class IndexModel : PageModel
    {
        private readonly AppDataContext _context;

        public IndexModel(AppDataContext context)
        {
            _context = context;
        }

        public IList<Movie> Movie { get; set; }

        public async Task OnGetAsync()
        {
            Movie = await _context.Movie.ToListAsync();
        }
    }
}
```


Pages/Movies/Index.cshtml



```html
@page
@model hello_app.Pages_Movies.IndexModel

@{
    ViewData["Title"] = "Index";
}

<h1>Index</h1>

<p>
    <a asp-page="Create">Create New</a>
</p>
<table class="table">
    <thead>
        <tr>
            <th>
                @Html.DisplayNameFor(model => model.Movie[0].Title)
            </th>
            <th>
                @Html.DisplayNameFor(model => model.Movie[0].ReleaseDate)
            </th>
            <th>
                @Html.DisplayNameFor(model => model.Movie[0].Genre)
            </th>
            <th>
                @Html.DisplayNameFor(model => model.Movie[0].Price)
            </th>
            <th></th>
        </tr>
    </thead>
    <tbody>
@foreach (var item in Model.Movie) {
        <tr>
            <td>
                @Html.DisplayFor(modelItem => item.Title)
            </td>
            <td>
                @Html.DisplayFor(modelItem => item.ReleaseDate)
            </td>
            <td>
                @Html.DisplayFor(modelItem => item.Genre)
            </td>
            <td>
                @Html.DisplayFor(modelItem => item.Price)
            </td>
            <td>
                <a asp-page="./Edit" asp-route-id="@item.ID">Edit</a> |
                <a asp-page="./Details" asp-route-id="@item.ID">Details</a> |
                <a asp-page="./Delete" asp-route-id="@item.ID">Delete</a>
            </td>
        </tr>
}
    </tbody>
</table>
```





</b>





# 2) Generated files:

These files are generated inside the *`Pages/Movies`* Directory.


<b>

1. Index.cshtml
2. Index.cshtml.cs
	- This shows a list of records
	- https://localhost:5001/Movies 

3. Create.cshtml
4. Create.cshtml.cs
	- This Creates a new record
	- https://localhost:5001/Movies/Create 


5. Details.cshtml
6. Details.cshtml.cs
	- This shows details of a single record
	- https://localhost:5001/Movies/Details?id=1 


7. Edit.cshtml
8. Edit.cshtml.cs
	- This edits a single record
	- https://localhost:5001/Movies/Edit?id=1 


9. Delete.cshtml
10. Delete.cshtml.cs
	- This deletes a single record
	- https://localhost:5001/Movies/Delete?id=1 



</b>


















