pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'python333333333333333333333333333333333 -m py_compile sources/add2vals.py sources/calc.py' 
                stash(name: 'compiled-results', includes: 'sources/*.py*') 
            }
        }
    }
}
