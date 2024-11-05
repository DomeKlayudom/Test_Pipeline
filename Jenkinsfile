pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'pip install -r requirements.txt'
                }
            }
        }

        stage('Run Unit Tests') {
            steps {
                script {
                    sh 'python -m unittest discover'
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/test_reports/*.xml', allowEmptyArchive: true
            junit '**/test_reports/*.xml'
        }
    }
}
