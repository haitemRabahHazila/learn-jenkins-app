// pipeline {
//     agent any   

//     stages {
//         stage('Build') {  
//             agent{
//                 docker{
//                     image 'node:18-alpine'
//                     reuseNode:true
//                 }
//             } 
//             steps {
//                 sh '''
//                 ls -la
//                 node --version
//                 npm --version
//                 npm ci
//                 npm run build
//                 ls -la
//                 '''

//             }
//         }
//     }
// }


pipeline {
    agent any   // Run on any available Jenkins agent

    stages {
        stage('Build') {  
            steps {
                bat '''
                dir
                node --version
                npm --version
                npm ci
                npm run build
                dir
                '''
            }
        }
        stage('Test') {
            steps {
                // Check if the file exists using a Windows command
                bat '''
                if exist build\\index.html (
                    echo File exists
                ) else (
                    echo File does not exist
                    exit /b 1
                )
                npm test 
                '''
            }
        }
    }
    post {
        always {
            junit 'test-result/junit.xml'
        }
    }
}
