## Summary

* [SonarQube local docker server](#sonarqube-local-docker-server)
* [Scan your project with SonarScanner](#scan-your-project-with-sonarscanner)
* [Scan your cpp project with SonarScanner](#scan-your-cpp-project-with-sonarscanner)

## SonarQube local docker server

### Prerequisites

- [Docker](https://www.docker.com/get-started)

### Setup SonarQube Server

1. Run the following command to start the SonarQube server:

```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube
```

2. You can now open your browser and go to [http://localhost:9000](http://localhost:9000/).
3. Log in with the default credentials: `admin` / `admin`.

[Back to top](#summary)

## Scan your project with SonarScanner

1. Retrieve the project token from the SonarQube server:
2. Go to the “Administration” tab.
3. Go to security > Tokens
4. Enter a name for your token and click on “Generate”.

### Using SonarScanner to scan the project

1. Download the [SonarScanner](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/) and extract it to a know location
2. Add it to your environment variables (PATH in Windows)
3. Verify your installation by opening a new shell and executing the command `sonar-scanner -h` .

You should get output like this:

```
usage: sonar-scanner [options]

Options:
-D,--define <arg>     Define property
-h,--help             Display help information
-v,--version          Display version information
-X,--debug            Produce execution debug output
```

4. Create a configuration file in your project's root directory called `sonar-project.properties`
5. Fill it like in the file below:

```
# must be unique in a given SonarQube instance
sonar.projectKey=ICE-tool1

# Path is relative to the sonar-project.properties file. Defaults to .
sonar.sources=src

# server URL
sonar.host.url=http://host.docker.internal:9000

# authentication token used to authenticate to SonarQube
sonar.login=8542358fa39f75d30ca699bc27c57335e047c162

# coverage analysis parameter. Must be set to the path of the report file
# produced by the coverage tool (here for python we use coverage)
sonar.python.coverage.reportPaths=coverage.xml
```

6. Type the following command in your terminal to start scanning your project

```bash
sonar-scanner
```

You can now go back to the SonarQube server and see the results of the scan.

### Using Docker to scan the project

1. Edit the following command by replacing `<project_key>` with the name of your project and `<token>` with the token you just generated:

```bash
docker run \
    --rm \
    -e SONAR_HOST_URL="http://host.docker.internal:9000" \
    -e SONAR_SCANNER_OPTS="-Dsonar.projectKey=<project_key>" \
    -e SONAR_TOKEN="<token>" \
    -v ".:/usr/src" \
    sonarsource/sonar-scanner-cli
```

2. Execute this command from the root directory of your project.

You can now go back to the SonarQube server and see the results of the scan.

[Back to top](#summary)

## Scan your cpp project with SonarScanner

### Prerequisites

- [Visual Studio](https://visualstudio.microsoft.com/downloads/) Installed
- SonarQube server running

### Getting started

#### A. Retrieving SonarQube Token

1. Connect to your SonarQube server
2. Click on you profile icon and then on `My Account`
3. Then click on `Security` tab
4. Enter a name for your token, select the appropriated `Type` and click on `Generate`.

#### B. Setting up the necessary tools

1. Download the [SonarScanner](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/) and extract it to a know location and add it to the PATH.
2. Verify your installation by opening a new shell and executing the command `sonar-scanner -h` .

You should get output like this:

```shell
usage: sonar-scanner [options]

Options:
-D,--define <arg>     Define property
-h,--help             Display help information
-v,--version          Display version information
-X,--debug            Produce execution debug output
```

3. Download build wrapper at the following link and add it to the PATH:

```text
{SONARQUBE_URL}/static/cpp/build-wrapper-win-x86.zip
```

4. Verify your installation by opening a new shell and executing the command `build-wrapper-win-x86-64.exe` .

You should get output like this:

```shell
build-wrapper, version 6.41.1 (win-x86-64)
Copyright (C) 2014-2022 SonarSource SA, info@sonarsource.com

Usage: build-wrapper-win-x86-64.exe --out-dir <output directory> <build command>
```

5. Add `MSBuild.exe` to the PATH, it should be located at the following address:

```text
C:\Program Files\Microsoft Visual Studio\2022\Enterprise\MSBuild\Current\Bin\
```

6. Check if MSBuild is working by opening a new shell and executing the command `MSBuild.exe`:

You should get output like this:

```shell
MSBuild version 17.9.5+33de0b227 for .NET Framework
Syntax:              MSBuild.exe [options] [project file | directory]

Description:         ...
```
#### C. Creating the Sonarscanner configuration file

1. Create a configuration file in your project's root directory called `sonar-project.properties`
2. Fill it like in the file below:

```
# must be unique in a given SonarQube instance
sonar.projectKey=project1

# Path is relative to the sonar-project.properties file. Defaults to .
sonar.sources=src

# server URL
sonar.host.url=http://host.docker.internal:9000

# authentication token generated on point A to authenticate to SonarQube
sonar.login=8542358fa39f75d30ca699bc27c57335e047c162

# build wrapper output directory
sonar.cfamily.build-wrapper-output=build_wrapper_output_directory
```

#### D. Building and scanning your project

1. Before starting using the wrapper and the scanner, build your project in `Release`

2. To use the build wrapper, change directory to the `/build` folder and execute the following command:

```shell
build-wrapper-win-x86-64.exe --out-dir ../build_wrapper_output_directory MSBuild.exe src/ProjectName.vcxproj /t:Rebuild /p:Configuration=Release
```

3. Then go back to the root of your project and run the following command to scan the project and send the collected data to Sonarqube:

```shell
sonar-scanner
```

Your project should now appear in SonarQube if the sonar analysis is successful.

[Back to top](#summary)