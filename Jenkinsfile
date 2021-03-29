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
                /* node ./Deploy.js -- If required, replace the blank Deploy.js with a custom deploy script. */
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
