# 1) C#



# 1) Creating a new project:


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









# 2) Run the project:


## 2-1) Just run the project:

<b>

```bash
dotnet run
```
</b>

## 2-2) Specify which project to run:

<b>

```bash
dotnet run --project "hello_world.csproj"
```
</b>



## 2-3) Running the project while watching changes:

<b>

```bash
dotnet watch run
```
</b>




















