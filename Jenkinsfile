
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code checked out successfully'
            }
        }

        stage('Verify Python') {
            steps {
                bat 'python --version'
            }
        }

        stage('Test') {
            steps {
                bat 'python -m unittest -v'
            }
        }

        stage('Package') {
            steps {
                bat 'python -m pip install --user setuptools'
                bat 'python setup.py sdist'

                archiveArtifacts artifacts: 'dist/*',
                                 fingerprint: true

                echo 'Python package created successfully!'
            }
        }
    }
}
