pipeline {
    agent any

    stages {
        stage("Clone repo") {
            steps { 
                git branch: 'main', url: 'https://github.com/jdht1992/jenkins-fastapi-test.git'
            }
        }
        stage("Install dependencies") {
            steps {
                sh 'python3 -m venv env'
                sh './env/bin/pip install --upgrade pip'
                sh './env/bin/pip install -r requirements.txt'
            }
        }
        stage("Run tests") {
            steps {
                sh './env/bin/pytest'
            }
        }
        stage("Run FastAPI app") {
            steps {
                sh 'nohup ./env/bin/python main.py &'
                echo 'FastAPI app should now be running.'
            }
        }
    }
}
