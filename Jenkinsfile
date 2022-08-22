node {
    stage('Build'){
        docker.image('python:2-alpine').inside {
            sh 'python -m py_compile sources/add2vals.py sources/calc.py'
        }
    }

    stage('Test') {
        docker.image('qnib/pytest').inside {
            sh 'py.test sources/test_calc.py'
        }
    }
    stage('Manual Approval'){
        docker.image('python:2-alpine').inside {
            input message: 'Lanjutkan ke tahap Deploy?'
        }
    }
    stage('Deploy') {
        sh 'ls -al'
        sh 'sh sources/deliver.sh' 
        sleep(60)
        sh 'sh sources/scripts/kill.sh'
    }
}