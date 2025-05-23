pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'python3 -m py_compile sources/add2vals.py sources/calc.py' 
                stash(name: 'compiled-results', includes: 'sources/*.py*') 
            }
        }
        stage('Test'){
            steps {
                sh 'py.test --junit-xml test-reports/results.xml sources/test_calc.py'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
        stage('Deliver'){
            step {
               sh 'pyinstaller --onefile sources/add2vals.py'
            }
            post{
               sucess {
                  archiveArtifacts 'dist/add2vals'
               }
            }
        }
    }
}
