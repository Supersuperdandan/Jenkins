pipeline {
    agent any
    stages {
        

        stage('install') {
            /* runtime-version */
            steps {
                bat 'npm install'
                bat 'npm install aws-sdk'
            }
        }

        stage('pre_build') {
            steps {
                echo "Running React UI build for @(owner.fullName.escape) @(project.name.escape)."
            }
        }

        stage('build') {
            steps {
                bat 'npm run build'
            }
        }
        
        stage('post_build') {
            steps {
                echo "@(owner.fullName.escape) @(project.name.escape) build completed on `date`"
            }
        }
            
        /* cache and artifacts*/
    }
}
