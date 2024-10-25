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
        stage('test'){
            bat '''
            test -f build/index.html
            npm test 
            '''
            
        }
    }
    post{
        always{
            junit 'test-result/junit.xml'
        }
    }
}
