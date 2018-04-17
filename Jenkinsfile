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
		        //sh 'mvn -Ddependency.check.format=XML -Ddependency.check.skip=false clean check'
                //dependencyCheckPublisher canComputeNew: true, canRunOnFailed: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: '', unstableTotalHigh: '0'
                            dependencyCheckAnalyzer datadir: '', hintsFile: '', includeCsvReports: false, includeHtmlReports: false, includeJsonReports: false, isAutoupdateDisabled: false, outdir: '', scanpath: '**/*.jar,**/pom.xml', skipOnScmChange: false, skipOnUpstreamChange: false, suppressionFile: '', zipExtensions: '',includeVulnReports: false

                            dependencyCheckPublisher canComputeNew: false, defaultEncoding: '', healthy: '85', pattern: '**/dependency-check-report.xml', shouldDetectModules: true, unHealthy: ''


            }
        }

        stage ('package') {

                    steps {
                            sh 'mvn package'
                    }
          }

    }
}