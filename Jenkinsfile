pipeline {
    agent any

    stages {
        stage("Clone repo") {
            steps {
                checkout scm
            }
        }
        stage("Install dependencies") {
            steps {
                sh 'python3 -m vnev env'
                sh '. env/bin/activate && pip install -r requirements.txt'
            }
        }
        stage("Run tests") {
            steps {
                sh '. env/bin/activate && pytest'
            }
        }
        stage("Run FastAPI app") {
            steps {
                sh '. env/bin/activate && python main.py &'
            }
        }

}
}
