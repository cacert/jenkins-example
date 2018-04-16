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

        stage ('Build'){
            steps {
                dependencyCheckPublisher canComputeNew: false, canRunOnFailed: true, defaultEncoding: '', healthy: '', pattern: '', unHealthy: '', unstableTotalHigh: '0'
            }
        }

    }
}