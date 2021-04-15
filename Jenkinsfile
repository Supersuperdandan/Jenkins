@()(implicit project: CbProject, owner: Owner)
version: 0.1

pipeline {
    agent { docker { image 'node:12' } }
    stages {
        stage('install') {
            steps {
                sh 'npm install'
                sh 'npm install aws-sdk'
            }
        }

        stage('pre_build') {
            steps {
                echo "Running React UI build for @(owner.fullName.escape) @(project.name.escape)."
            }
        }

        stage('build') {
            steps {
                sh 'npm run build'
            }
        }
        
        stage('post_build') {
            steps {
                echo "@(owner.fullName.escape) @(project.name.escape) build completed on `date`"
            }
        }
           
    }
   
    post {
        always {
            archiveArtifacts artifacts: 'build/**/*', fingerprint: true
        }
    }
}
