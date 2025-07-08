pipeline {
    agent any

    environment {
        JAVA_HOME = "C:\\Program Files\\Java\\jdk-21"
        TALEND_CLI = "C:\\Talend\\Talend-Studio-win-x86_64"
        JOB_NAME = "CI_CD_DEMO_PROJECT"
    }

    parameters {
        string(name: 'CSV_FILE_PATH', defaultValue: 'C:/Users/home/Downloads/customers2.csv')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/rags7505/talend-ci-example1.git'
            }
        }

        stage('Unzip Job') {
            steps {
                bat 'powershell -Command "Expand-Archive -Force CustomerLoggerJob_0.1.zip .\\job2"'
            }
        }

        stage('Run Talend Job') {
            steps {
                bat '''
                    cd job2\\CustomerLoggerJob
                    call CustomerLoggerJob_run.bat --context=Default --context_param CSV_FILE_PATH=%CSV_FILE_PATH%
                '''
            }
        }
    }
}
