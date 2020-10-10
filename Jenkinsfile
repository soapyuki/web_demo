pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '68f25611-b375-47b9-9a31-f28e782c3e9c', url: 'git@github.com:soapyuki/web_demo.git']]])
            }
        }
        stage('build') {
            steps {
                sh label: '', script: 'mvn clean package'
            }
        }
        stage('deploy') {
            steps {
                deploy adapters: [tomcat8(credentialsId: '8c1d8231-8097-4273-98c7-3f41ae3624ee', path: '', url: 'http://192.168.219.130:8080')], contextPath: null, war: 'target/*.war'
            }
        }   
    }
}
