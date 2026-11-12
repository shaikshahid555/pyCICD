pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main',
          url: 'https://github.com/shaikshahid555/pyCICD.git'
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
      }
    }
  }
}
post {
  success {
    archiveArtifacts artifacts: 'dist/*',
      fingerprint: true
    echo 'Python CI/CD Pipeline completed successfully!'
  }
  failure {
    echo 'Pipeline failed. Check the console output.'
  }
}
