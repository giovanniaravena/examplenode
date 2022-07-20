@Library('VeracodeSharedLib') _
pipeline {
    agent any
    stages {
        stage('Deliver for development') {
            when {
                branch 'develop'
            }
            steps {
                sh './jenkins/scripts/deliver-for-development.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'main'
            }
            // failFast true
            // parallel {
            stages{

                stage('Build'){
                    // agent {
                    //     label "for-branch-a"
                    // }
                    steps {
                        echo "Build Node JS"
                        echo "Build Node JS2"
                                               
                    }
                }
                stage('Upload Scan'){
                    // agent {
                    //     label "for-uploadscan"
                    // }
                    steps {
                        sh 'ls'
                        sh 'pwd'
                        if (fileExists('test.zip')) {
                            sh 'rm test.zip'
                        } 
                        zip zipFile: 'test.zip', archive: false, dir: ''
                        archiveArtifacts artifacts: 'test.zip', fingerprint: true
                        
                        
                        
                        // script{
                        //   policyScanLib.uploadArtifact(ApplicationName: "Demo", UploadIncludesPattern: "test.zip", Id: 'b42d9a0dc0502a2c2ac0f19a8d9d8bf9', Key: 'eaacc0db208b00a9750441fb3e8b1eade495e63bde69f89b0447d83924becdf49e50a2e89e9fa1f398b7b3ab037333a7f4aee17765f613a5b78f247c5af9a94b')
                        // }
                        veracode applicationName: "Demo", canFailJob: true, criticality: 'VeryHigh', debug: true, deleteIncompleteScan: true, fileNamePattern: '', replacementPattern: '', createSandbox: false, sandboxName: '', scanExcludesPattern: '', scanIncludesPattern: '', scanName: '', teams: '', timeout: 60, uploadIncludesPattern: "test.zip", vid: "b42d9a0dc0502a2c2ac0f19a8d9d8bf9", vkey: "eaacc0db208b00a9750441fb3e8b1eade495e63bde69f89b0447d83924becdf49e50a2e89e9fa1f398b7b3ab037333a7f4aee17765f613a5b78f247c5af9a94b", waitForScan: false
                        // veracode applicationName: 'Demo', canFailJob: true, createSandbox: true, criticality: 'VeryHigh', debug: true, fileNamePattern: '', replacementPattern: '', sandboxName: 'TestJenkins2', scanExcludesPattern: '', scanIncludesPattern: '', scanName: 'scan', teams: '', uploadIncludesPattern: 'test.zip', vid: 'b42d9a0dc0502a2c2ac0f19a8d9d8bf9', vkey: 'eaacc0db208b00a9750441fb3e8b1eade495e63bde69f89b0447d83924becdf49e50a2e89e9fa1f398b7b3ab037333a7f4aee17765f613a5b78f247c5af9a94b'
                        // veracode applicationName: 'Demo', canFailJob: true, criticality: 'VeryHigh', debug: true, fileNamePattern: '', replacementPattern: '', sandboxName: 'TestJenkins', scanExcludesPattern: '', scanIncludesPattern: '', scanName: '', teams: '', uploadIncludesPattern: 'test.zip', vid: 'b42d9a0dc0502a2c2ac0f19a8d9d8bf9', vkey: 'eaacc0db208b00a9750441fb3e8b1eade495e63bde69f89b0447d83924becdf49e50a2e89e9fa1f398b7b3ab037333a7f4aee17765f613a5b78f247c5af9a94b'
                    
                    }
                }
                
            }
        }
    }
}  