pipeline {
    agent any
    stages {
        

        stage('install') {
            /* runtime-version */
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
           

        
        /* artifacts */
    }
    
    cache(maxCacheSize: 250, caches: [[$class: 'ArbitraryFileCache', path: 'node_modules/**/*']])
}
