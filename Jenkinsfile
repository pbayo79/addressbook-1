pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script{
                    echo "Compiling the job"
                }
            }
        }
        stage('UnitTest') {
            steps {
                script{
                    echo "running the code"
                }
            }
        }
        stage('Package') {
            steps {
                script{
                    echo "Packaging the code"
                }
            }
        }
    }
}
