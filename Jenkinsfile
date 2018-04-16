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
                sh "/tools/run :maven -- mvn -P jenkins -B -Ddependency.check.format=XML -Ddependency.check.skip=false clean verify "
                dependencyCheckPublisher canComputeNew: false, canRunOnFailed: true, defaultEncoding: '', healthy: '', pattern: '', unHealthy: '', unstableTotalHigh: '0'
            }
        }

    }
}