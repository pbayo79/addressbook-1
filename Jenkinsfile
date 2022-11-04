pipeline {
    agent none
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }

    stages {
        stage('Compile') {
            agent any
            steps {
                script {
                    echo "Compiling the job"
                    git 'https://github.com/pbayo79/addressbook-1.git'
                    sh 'mvn compile'
                }
            }
        }
        stage('UnitTest') {
            agent any
            steps {
                script {
                    echo "Running the test cases"
                    git 'https://github.com/pbayo79/addressbook-1.git'
                    sh 'mvn test'
                }
            }
        }
        stage('Package') {
            agent any
            steps {
                script {
                    sshagent(['build-server-key']) {
                    echo "Packaging the code" 
                    sh "scp =o StrictHostKeyChecking=no server-script.sh ec2-user@172.31.22.177:/home/ec2-user"
                    sh "ssh =o StrictHostKeyChecking=no ec2-user@172.31.22.177 'bash ~/server-script.sh'"

                    }
                    
                }
            }
        }
    }
}    
 
