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















