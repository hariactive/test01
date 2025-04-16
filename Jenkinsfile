pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/hariactive/test01.git'
            }
        }

        stage('Set Up Virtual Environment') {
            steps {
                sh '''
                    python3 -m venv venv
                    ./venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Run Flask App') {
            steps {
                sh '''
                    nohup ./venv/bin/python3 app.py > flask.log 2>&1 &
                    sleep 5
                '''
            }
        }

        stage('Test App') {
            steps {
                script {
                    def result = sh(script: "curl -f http://localhost:5000", returnStatus: true)
                    if (result != 0) {
                        error("❌ Flask app not running!")
                    } else {
                        echo "✅ Flask app is running!"
                    }
                }
            }
        }

        stage('View Flask Logs') {
            steps {
                sh 'cat flask.log || echo "No log file found."'
            }
        }
    }
}
