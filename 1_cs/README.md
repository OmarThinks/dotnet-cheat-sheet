# 1) C#




# 1) About:
**C-Sharp**.  
Maintained by Micrsoft.  
Used for several applications, like web apps, AI and 3D.  
Here we will talk about web applications only.




# 2) Creating a new project:


<b>

```bash
dotnet new console
```
Or:
```bash
dotnet new console --name "hello_world"
```

</b>

Now, Change directory, to get to the 
directory of the project:

<b>

```bash
cd hello_world/
```
</b>



Now the structure of the files looks like this:
<b>

```
hello_world
	|-obj
	|	|-
	|	|-
	|-hello_world.csproj
	|-Program.cs
```
</b>









# 3) Run the project:



<b>

Just run the project:
```bash
dotnet run
```

---

Specify which project to run:

```bash
dotnet run --project "hello_world.csproj"
```

---

Running the project while watching changes:
```bash
dotnet watch run
```
</b>




















