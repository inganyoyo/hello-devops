pipeline {
    agent {
        kubernetes {
          yamlFile 'builder.yaml'
        }
      }
    stages {
        // git에서 repository clone
        stage('Prepare') {
          steps {
            echo 'Clonning Repository'
            container('maven'){
            git url: 'https://github.com/inganyoyo/hello-devops.git',
              branch: 'main'
              //credentialsId: '생성한 github access token credentail id'
            }
            }
        }

        stage ('unit test') {
            steps {
                container('maven') {
                    sh './hello-springboot-mvn/mvn -B -Dmaven.test.failure.ignore verify'
                }
            }
        }
    }
}