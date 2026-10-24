
pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application'
                bat 'python --version'
                bat 'python -m py_compile app.py test_app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Running automated tests'
                bat 'python -m unittest -v'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application'
                bat 'if not exist deploy mkdir deploy'
                bat 'copy /Y app.py deploy\\app.py'
                bat 'python deploy\\app.py'
            }
        }
    }
}
