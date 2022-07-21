@Library('VeracodeSharedLib') _
pipeline {
    agent any
    stages {
        
        stage('Git') {
            steps{
                withCredentials([gitUsernamePassword(credentialsId: 'f433e67d-629a-4e8c-9804-550f6322b13f', gitToolName: 'git-tool')]) {
                    sh 'git fetch --all'
                }
            }
        }
        stage('Build') {
            steps {
                echo "Build Node JS"             
            }
        }
        stage('Upload and Scan') {
            // failFast true
            // parallel {
            stages{
                stage('Artifact'){
                    // agent {
                    //     label "for-branch-a"
                    // }
                    steps {
                        sh 'ls'
                        sh 'pwd'
                        zip archive: true, dir: '', exclude: '', glob: '', overwrite: true, zipFile: 'policyscan.zip'         
                        sh 'ls'
                    }
                }
                stage('Upload Scan'){
                    // agent {
                    //     label "for-branch-b"
                    // }
                    steps {
                        // script{
                        //   policyScanLib.uploadArtifact(ApplicationName: "Demo", UploadIncludesPattern: "test.zip", Id: 'b42d9a0dc0502a2c2ac0f19a8d9d8bf9', Key: 'eaacc0db208b00a9750441fb3e8b1eade495e63bde69f89b0447d83924becdf49e50a2e89e9fa1f398b7b3ab037333a7f4aee17765f613a5b78f247c5af9a94b')
                        // }
                        veracode applicationName: "Demo", canFailJob: true, criticality: 'VeryHigh', debug: true, deleteIncompleteScan: true, fileNamePattern: '', replacementPattern: '', createSandbox: false, sandboxName: '', scanExcludesPattern: '', scanIncludesPattern: '' , teams: '', timeout: 60, uploadIncludesPattern: "policyscan.zip", vid: "b42d9a0dc0502a2c2ac0f19a8d9d8bf9", vkey: "eaacc0db208b00a9750441fb3e8b1eade495e63bde69f89b0447d83924becdf49e50a2e89e9fa1f398b7b3ab037333a7f4aee17765f613a5b78f247c5af9a94b", waitForScan: false
                        // veracode applicationName: 'Demo', canFailJob: true, createSandbox: true, criticality: 'VeryHigh', debug: true, fileNamePattern: '', replacementPattern: '', sandboxName: 'TestJenkins2', scanExcludesPattern: '', scanIncludesPattern: '', scanName: 'policyscan', teams: '', uploadIncludesPattern: 'policyscan.zip', vid: 'b42d9a0dc0502a2c2ac0f19a8d9d8bf9', vkey: 'eaacc0db208b00a9750441fb3e8b1eade495e63bde69f89b0447d83924becdf49e50a2e89e9fa1f398b7b3ab037333a7f4aee17765f613a5b78f247c5af9a94b'
                        // veracode applicationName: 'Demo', canFailJob: true, criticality: 'VeryHigh', debug: true, fileNamePattern: '', replacementPattern: '', sandboxName: 'TestJenkins', scanExcludesPattern: '', scanIncludesPattern: '', scanName: '', teams: '', uploadIncludesPattern: 'policyscan.zip', vid: 'b42d9a0dc0502a2c2ac0f19a8d9d8bf9', vkey: 'eaacc0db208b00a9750441fb3e8b1eade495e63bde69f89b0447d83924becdf49e50a2e89e9fa1f398b7b3ab037333a7f4aee17765f613a5b78f247c5af9a94b'
                    }
                }
                
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy Node JS"             
            }
        }
    }
}  