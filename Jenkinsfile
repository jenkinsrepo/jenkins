pipeline {
    agent any 
    stages {
        stage('checkout') { 
            steps {
                git 'https://github.com/rnstech21/warrepo.git'

            }
        }
        stage('Build') { 
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('deploy s3') { 
        steps {
            s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'demo985', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-1', showDirectlyInBrowser: false, sourceFile: '**/*.war', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'SUCCESS', profileName: 's3bucket', userMetadata: []
        }
        }
    }
}
