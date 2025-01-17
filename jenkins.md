## Summary

**-> [Back to Index](./README.md)**

* [Pipeline structure](#pipeline-structure)
* [Credentials Management](#credentials-management)

## Pipeline structure

Here is the Jenkins declarative pipeline structure:

```groovy
pipeline {
 agent {
     // Define where the pipeline will run
     // Possible values: any, none, label, agent, docker, dockerfile, kubernetes
 }
 options {
     // Define pipeline options
     // Possible values: buildDiscarder, disableConcurrentBuilds, skipDefaultCheckout, timeout
 }
 environment {
     // Define environment variables
     // Example: FOO = "bar"
 }
 parameters {
     // Define pipeline parameters
     // Example: string(name: 'PARAM_NAME', defaultValue: 'default', description: 'Description')
 }
 stages {
     // Define pipeline stages
     stage('Stage Name') {
         steps {
             // Define steps to be executed in this stage
             // Example: sh 'echo "Hello, World!"'
         }
     }
 }
 post {
     // Define post-build actions
     // Example: always, changed, failure, success, unstable, cleanup
 }
}
```

https://www.jenkins.io/doc/

[Back to top](#summary)

## Credentials Management

Windows:

```groovy
pipeline {
    agent any
    environment {
        EXAMPLE_CREDS = credentials('example-credentials-id')
    }
    stages {
        stage('Example') {
            steps {
                bat('curl -u %EXAMPLE_CREDS_USR%:%EXAMPLE_CREDS_PSW% https://example.com/')
            }
        }
    }
}
```

Linux:

```groovy
pipeline {
    agent any
    environment {
        EXAMPLE_CREDS = credentials('example-credentials-id')
    }
    stages {
        stage('Example') {
            steps {
                sh('curl -u $EXAMPLE_CREDS_USR:$EXAMPLE_CREDS_PSW https://example.com/')
            }
        }
    }
}
```

https://www.jenkins.io/doc/book/pipeline/jenkinsfile/#combining-credentials-in-one-step

[Back to top](#summary)