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
				dependencyCheckAnalyzer includeCsvReports: false, includeHtmlReports: true, includeJsonReports: false
				dependencyCheckPublisher canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: '', unstableTotalAll: '5', unstableTotalHigh: '2', unstableTotalLow: '2', unstableTotalNormal: '2'
            }
        }

    }
}