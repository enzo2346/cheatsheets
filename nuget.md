## Summary

* [NuGet in Visual Studio](#nuget-in-visual-studio)
* [NuGet CLI](#nuget-cli)
* [Useful links](#useful-links)

## NuGet in Visual Studio

1. Open a C++ project in Visual Studio

2. Right click on solution and select `Manage Nuget Packages for Solution`

3. Search for your packet in `Browse`, then select it, choose the version and on which project to install it and finally click on install

4. Your packet will be installed at the following location:

```txt
C:\Users\<USER>\.nuget\packages
```

[Back to top](#summary)

## NuGet CLI

1. Download [NuGet](https://learn.microsoft.com/en-us/nuget/reference/nuget-exe-cli-reference?tabs=windows#installing-nugetexe) and add it to the PATH

2. At the root of the repo type the following command to install a package:

```shell
nuget install <packageName> -Version <versionNumber>
```

[Back to top](#summary)

## Useful links

https://learn.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio

https://learn.microsoft.com/en-us/nuget/reference/nuget-exe-cli-reference?tabs=windows

[Back to top](#summary)