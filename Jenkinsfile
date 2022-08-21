// node {
//     docker.image('python:2-alpine').inside {
//         stage('Build') {
//             sh 'pwd'
//             sh 'ls -al'
//             sh 'python -m py_compile /sources/add2vals.py /sources/calc.py'
//         }
//     }
// }

pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                }
            }
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py'
            }
        }
    }
}
