# AWS SDK for Unity

This is just a dummy repo to be able to download and prepare the AWS SDK for
.NET to use in Unity. See
[`aws/aws-sdk-net`](https://github.com/aws/aws-sdk-net) for information about
the packages.

1. Create an empty folder (this repo) and run the following

   ```bash
   dotnet new classlib -f netstandard2.0
   ```

2. Add packages to the project

   ```bash
   dotnet add package AWSSDK.PackageYouWant
   ```

3. Build the release

   ```bash
   dotnet publish -c Release
   ```

4. Copy the DLLs from `./bin/Release/netstandard2.0/publish` to
   `<chloe-unity>/Assets/Plugins/AWSSDK`

   ```bash
   cp ./bin/Release/netstandard2.0/publish <chloe-unity>/Assets/Plugins/AWSSDK
   ```

You may need to add a `link.xml` file to your Assets folder due to IL2CPP
stripping:

```xml
<linker>
    <assembly fullname="AWSSDK.Core" preserve="all"/>
    <assembly fullname="AWSSDK.PackageYouWant" preserve="all"/>
</linker>
```
