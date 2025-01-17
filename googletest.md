This documentation provides step-by-step instructions on how to use GoogleTest with Conan in a C++ project.

## Summary

* [Prerequisites](#prerequisites)
* [Setting up GoogleTest with Conan](#setting-up-googletest-with-conan)
* [Using GoogleTest with Ctest](#using-googletest-with-ctest)
* [Using GoogleTest with Visual Studio](#using-googletest-with-visual-studio)
* [Using GoogleTest with vstest.console.exe](#using-googletest-with-vstestconsoleexe)
* [Useful links](#useful-links)

## Prerequisites

- C++ compiler (e.g., GCC, Clang, MSVC)
- Conan package manager (https://conan.io/)
- CMake build system (https://cmake.org/)
- C++ Project with a library called by a main

[Back to top](#summary)

## Setting up GoogleTest with Conan

1. At the root of your project, create the file conanfile.txt with the following content:

```txt
[requires]
gtest/1.14.0

[generators]
CMakeDeps
CMakeToolchain
```

2. Add to the main CMakeLists.txt the following lines:

```txt
enable_testing()
add_subdirectory(test)
```

3. Create a directory `test` where you will create your UT

4. Inside this directory, create a cpp file to write your tests with the following structure (here called `tests.cpp`)

```cpp
#include <headerofthefiletotest.h>
#include <gtest/gtest.h>

// Demonstrate some basic assertions.
TEST(testExample1, BasicAssertions) {
  // Expect two strings not to be equal.
  EXPECT_STRNE("hello", "world");
  // Expect equality.
  EXPECT_EQ(7 * 6, 42);
}

int main(int argc, char** argv)
{
    testing::InitGoogleTest(&argc, argv);
    return RUN_ALL_TESTS();
}

```

5. In the same directory, create a CMakeLists.txt with the following content: (replace LibToTest with the library you want to test)

```txt
find_package(GTest CONFIG REQUIRED)

add_executable(unit_tests
    tests.cpp
)

target_link_libraries(unit_tests PRIVATE
    <LibToTest>
    GTest::gtest_main

add_test(all unit_tests)
```

6. You can now build the project the way you are used to with Conan and CMake, here is an example of how to do it:

```shell
conan install . -s build_type=Debug -s compiler.cppstd=20 --output-folder=build --build missing
cmake -S . -B build
cmake --build build
```

7. You can now start the tests by executing the .exe generated in the build folder:

```shell
.\unit_tests.exe
```

[Back to top](#summary)

## Using GoogleTest with Ctest

After building the tests like in `getting started`, you can launch the tests in the build folder with Ctest with the following command:

```shell
ctest -V
```

[Back to top](#summary)

## Using GoogleTest with Visual Studio

Remark: To use test coverage in Visual studio, you need to have `Visual Studio Enterprise` Edition and to build the project in `Debug`

After building the tests like in `getting started`, you can launch the tests and the code coverage analysis in Visual Studio by doing the following steps:

1. Open the project in Visual Studio

2. Select from the top bar `Test`, then select `Processor Architecture for AnyCPU Projects`, then select`x64`

3. Then select from the top bar `Test`, then select `Run All Tests`

4. Then select from the top bar `Test`, then select `Analyse Code Coverage for All Tests`

5. Then select from the Code Coverage Results menu, you can export the results in differents format by clicking on `Export Results`

[Back to top](#summary)

## Using GoogleTest with vstest.console.exe

Remark: 
To use test coverage in vstest.console.exe, you need to build the project in `Debug`, and to have installed `GoogleTestAdapter` (GTA).
GTA is installed by default with `Desktop development with C++` as an extension and can also being installed with Nuget packages.
Here is the location of GTA TestAdapterPath:

```shell
C:\Users\<USER>\.nuget\packages\googletestadapter\0.18.0\build\_common\                       # NuGet package installed with Visual Studio
C:\Program Files\Microsoft Visual Studio\2022\Enterprise\Common7\IDE\Extensions\wco0lb2z.rf0  # Visual Studio Extension
.\GoogleTestAdapter.0.18.0\build\_common                                                      # `nuget install googletestadapter -Version 0.18.0` at the root of the repo
```

Remark: the folder `\wco0lb2z.rf0` is a hash that may vary between devices

If the prerequisites are fullfield, you can run the tests and the code coverage analysis with the following command:

```shell
vstest.console.exe "pathtoexeordll\unit_tests.exe" /TestAdapterPath:"C:\Users\<USER>\.nuget\packages\googletestadapter\0.18.0\build\_common\" /Logger:html /EnableCodeCoverage /Collect:"Code Coverage;Format=Xml" /ResultsDirectory:"tests_results"
```

Here are others options to print the logs instead of html: console / trx / json / xml / teamcity

[Back to top](#summary)

## Useful links

Googletest Conan recipe:
https://conan.io/center/recipes/gtest

Example of usage of googletest:
https://github.com/rutura/CMakeSeries/tree/main/Ep032/conan-template

Googletest doc:
http://google.github.io/googletest/quickstart-cmake.html

vstest.console.exe doc:
https://learn.microsoft.com/en-us/visualstudio/test/vstest-console-options?view=vs-2022

GoogleTestAdapter trouble shooting page:
https://github.com/microsoft/TestAdapterForGoogleTest?tab=readme-ov-file#trouble_shooting

[Back to top](#summary)