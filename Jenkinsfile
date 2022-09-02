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
              //credentialsId: '생성한 github access token credentail id' --dd
            }
            }
        }

        stage ('unit test') {
            steps {
                container('maven') {
                    dir ('./hello-springboot-mvn'){
                        sh """
                        mvn -version
                        ./mvn -Dmaven.test.failure.ignore verify
                        """
                    }
                }
            }
        }
    }
}
