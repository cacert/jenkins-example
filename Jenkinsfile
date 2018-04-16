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
				dependencyCheckAnalyzer  hintsFile: '', includeCsvReports: false, includeHtmlReports: true, includeJsonReports: false, includeVulnReports: true, isAutoupdateDisabled: true, outdir: '', scanpath: '', skipOnScmChange: true, skipOnUpstreamChange: true, suppressionFile: '', zipExtensions: ''
				dependencyCheckPublisher canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: '', unstableTotalAll: '5', unstableTotalHigh: '2', unstableTotalLow: '2', unstableTotalNormal: '2'
            }
        }

    }
}