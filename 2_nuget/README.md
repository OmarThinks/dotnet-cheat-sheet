# 2) NuGet:



# 1) Website:


**https://www.nuget.org/**




# 2) Installing a package:

<b>

```bash
dotnet add package Humanizer
```
</b>

To make sure that the package has been installed successfully to the project, check the file **`hello_world.csproj`**,
you should find these lines:

<b>

```xml
<ItemGroup>
	<PackageReference Include="Humanizer" Version="2.9.9" />
</ItemGroup>
```
</b>





# 3) Using Installed Packages:



<b>

```c#
using Humanizer;
```
Now you can use all the functions in this package.

</b>


# 4) Listing installed packages:

<b>

```bash
dotnet list package
```
To get a list of the packages installed in this project.

---

```bash
dotnet list package --outdated
```
Get a list of packages that need to be updated


</b>








# 5) Uninstalling a package:
<b>

```bash
dotnet remove package Humanizer
```

</b>





