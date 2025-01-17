## Summary

**-> [Back to Index](./README.md)**

* [Install](#install)
* [Build Project](#build-project)
* [Profiles](#profiles)
* [Env](#env)

## Install

1. Download Python 3.11.4 or newer from https://www.python.org/
2. Install it and add it to the PATH
3. Execute the following command in a terminal to install conan:

```
pip install --upgrade conan
```

4. Run any conan command to get the .conan2 folder created:

```
conan search poco --remote=conancenter
```

5. Create a profile for your user:

```
conan profile detect --force
```

If the detect profile is wrong, you can locate the profile file with the following command to edit it:

```
conan profile path default
```

Doc link: https://docs.conan.io/2/installation.html

[Back to top](#summary)

## Build Project

1. Install libraries, generate the files that CMake needs to find these libraries and to build the project (in the folder /build):

```
conan install . --output-folder=build --build=missing
```

2. Generate the project buildsystem:

```
cmake -S . -B build -G "Visual Studio 17 2022" -DCMAKE_TOOLCHAIN_FILE="conan_toolchain.cmake"
```

3. Build the project: 
```
cmake --build build --config Release
```

4. Run the app (here called compressor):

```
Release\compressor.exe
```

Made using this Conan tutorial: [Build a simple CMake project using Conan](https://docs.conan.io/2/tutorial/consuming_packages/build_simple_cmake_project.html#build-a-simple-cmake-project-using-conan)

And this CMake doc: https://cmake.org/cmake/help/latest/manual/cmake.1.html

[Back to top](#summary)

## Profiles

Conan profiles allow users to set a complete configuration set for settings, options, environment variables (for build time and runtime context), tool requirements, and configuration variables in a file.

A default profile will be created during the installation process. (`conan profile detect`)

To create a new profile, you can type the following command:

```
conan profile detect --name myprofile
```

You can then find the profile location with the following command to edit it:

```
conan profile path myprofile 
```

Profile files can be used with `-pr`/`--profile` option in many commands like conan install or conan create commands.

```
conan install . -pr=myprofile
```

Profiles can be located in different folders:

```
conan install . -pr /abs/path/to/myprofile   # abs path
conan install . -pr ./relpath/to/myprofile   # resolved to current dir
conan install . -pr ../relpath/to/myprofile  # resolved to relative dir
conan install . -pr myprofile  # resolved to [CONAN_HOME]/profiles/myprofile
```

List profiles:

```
conan profile list
```

Show profile content:

```
conan profile show -pr myprofile
```

Doc link: https://docs.conan.io/2/reference/config_files/profiles.html

[Back to top](#summary)

## Env

### VirtualBuildEnv 

VirtualBuildEnv is a generator that produces a conanbuildenv .bat, .ps1 or .sh script containing the environment variables of the build time context.

Here is an example with tool_requires in the conanfile.txt with cmake:

```
[tool_requires]
cmake/3.22.6
```

After executing the `conan install` command, it will generate a new file called `conanbuild.sh/bat/ps1` and a file `deactivate_conanbuild.sh/bat/ps1` in the build folder.

Execute `conanbuild.sh/bat/ps1` before building to activate the virtual environment and set some environment variables (for example here a new PATH that we can use to inject to our environment the location of CMake v3.22.6).

Execute `deactivate_conanbuild.sh/bat/ps1` after building to deactivate the virtual environment.

Doc: https://docs.conan.io/2/reference/tools/env/virtualbuildenv.html#virtualbuildenv


### VirtualRunEnv

TODO

Doc: https://docs.conan.io/2/reference/tools/env/virtualrunenv.html

[Back to top](#summary)