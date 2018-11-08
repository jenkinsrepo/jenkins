pipeline {
    agent any
    stages {
        stage('checkout') { 
            steps {
                git 'https://github.com/cloudtech12/petapp.git'

            }
        }
        stage('Build') { 
            steps {
                sh 'mvn clean package'
            }
        }
        stage('s3 Deploy') { 
            steps {
        s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'demo985', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-1', showDirectlyInBrowser: false, sourceFile: '**/*.war', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'SUCCESS', profileName: 'bucket', userMetadata: []
            }
        }
    }
}
