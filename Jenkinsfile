pipeline {
    agent any

    tools {
        maven 'maven_3_5_0'
    }

    stages {
        stage ('Compile Stage') {

            steps {
                    sh 'mvn clean compile'
            }
        }

        stage ('Testing Stage') {

            steps {
                    sh 'mvn test'
            }
        }

        stage ('OWASP Dependency Check'){
            steps {
		        sh 'mvn -Ddependency.check.format=XML -Ddependency.check.skip=false clean verify'
               dependencyCheckPublisher canComputeNew: false, canRunOnFailed: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: '', unstableTotalHigh: '0'
            }
        }

        stage ('package') {

                    steps {
                            sh 'mvn package'
                    }
          }

    }
}