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

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    sh '/usr/bin/cf --help'
                    sh '/usr/bin/cf login -a https://api.cf.eu10.hana.ondemand.com -u $USERNAME -p $PASSWORD'
                    sh '/usr/bin/cf push'
                }
            }

        }

    }

}
