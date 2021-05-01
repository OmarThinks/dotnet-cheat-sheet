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






# 3) Listing installed packages:

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

















