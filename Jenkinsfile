pipeline {
    agent any 
    stages {
        stage('GITHUB') { 
            steps {
                echo "This is my SCM Job"
                git credentialsId: 'e059cf1e-0e5b-4ff3-b193-414652030158', url: 'https://github.com/krishnavagu/lappy-project.git'
            }
        }
        stage('Build') { 
            steps {
                echo "This is my Build Job"
                sh label: '', script: 'mvn clean package'
            }
        }
        stage('Test') { 
            steps {
                echo "This is my Test job"
            }
        }
        stage('Deploy') { 
            steps {
                echo "This is my Deployment job"
                deploy adapters: [tomcat9(credentialsId: 'TomcatDeployment', path: '', url: 'http://54.163.10.210:8085/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
