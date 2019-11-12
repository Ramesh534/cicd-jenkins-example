pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_6_0') {
                    sh 'mvn -version'
                    sh 'mvn clean package'
                }
            }
        }

    }

}
