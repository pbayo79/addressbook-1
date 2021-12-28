pipeline {
    agent any
    parameters{
        string(name:'Env',defaultValue:'Test',description:'version to deploy')
        booleanParam(name:'executeTests',defaultValue: true,description:'decide to run tc')
        choice(name:'BRANCH',choices:['1.1','1.2','1.3'])
    }
    environment{
        NEW_VERSION = '2.1'
    }
    stages {
        stage('Compile') {
            steps {
                script{
                    echo "Compiling the code"
                  }
            }
        }
        stage('UnitTest') {
            when{
                expression{
                    params.executeTests == true
                }
            }
            steps {
                script{
                    echo "Running the test cases"
                }
            }
        }
        stage('Package') {
            input{
                message "Select the version to package"
                ok "Version selected"
                parameters{
                    choice(name:'NEWAPP',choices:['1.2','2.1','3.1'])
                }
            }
            steps {
                script{
                    echo "Packaging thr code"
                    echo "Packaging version ${NEW_VERSION}"
                }
            }
        }
        stage('Deploy') {
           steps {
                script{
                    echo "Deploying the app"
                    echo "Deploying to env: ${params.Env}"
                    echo "Deploying the app version ${params.APPVERSION}"
                }
            }
        }
    }
}