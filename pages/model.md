# Creating a model:



`/Models/Pizza.cs`

```cs
namespace ContosoPizza.Models;

public class Pizza
{
    public int Id { get; set; }
    public string? Name { get; set; }
    public bool IsGlutenFree { get; set; }
}
```


`/Data/PizzaContext.cs`

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.EntityFrameworkCore;
using ContosoPizza.Models;

namespace ContosoPizza.Data;

public class PizzaContext : DbContext
{
    public PizzaContext (DbContextOptions<PizzaContext> options)
        : base(options)
    {
    }

    public DbSet<ContosoPizza.Models.Pizza> Pizza { get; set; } = default!;
}
```


`Program.cs`


```cs
using Microsoft.EntityFrameworkCore;
using Microsoft.Extensions.DependencyInjection;
using ContosoPizza.Data;
var builder = WebApplication.CreateBuilder(args);

var connectionString = builder.Configuration.GetConnectionString("pizzas") ?? "Data Source=pizzas.db";
builder.Services.AddDbContext<PizzaContext>(options => options.UseSqlite(connectionString));

// OR
var builder = WebApplication.CreateBuilder(args);
builder.Services.AddDbContext<ContosoPizzaContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("ContosoPizzaContext") ?? throw new InvalidOperationException("Connection string 'ContosoPizzaContext' not found.")));
```

