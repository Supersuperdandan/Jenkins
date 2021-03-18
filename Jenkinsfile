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
                /* sh 'npm run build' */
                /* node ./Deploy.js -- If required, replace the blank Deploy.js with a custom deploy script. */
            }
        }
        
        stage('post_build') {
            steps {
                echo "@(owner.fullName.escape) @(project.name.escape) build completed on `date`"
            }
        }
           
        /* artifacts */
    }
    
    
    post {
        always {
            cache(maxCacheSize: 250, caches: [[$class: 'ArbitraryFileCache', path: 'node_modules/**/*']])
        }
    }
    
    post {
        always {
            artifact('@(owner.usernameLC)_@(project.code)', save_to_dir(build/**/*))
        }
    }
    
}
