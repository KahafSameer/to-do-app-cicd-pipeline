pipeline {
    agent any
   
    environment{
        SCANNER_HOME= tool 'sonar-scanner'
    }

    stages {
        stage('git-checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/KahafSameer/to-do-app-cicd-pipeline'
            }
        }

    stage('Sonar Analysis') {
            steps {
                   sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.url=http://13.53.38.49:9000/ -Dsonar.login=squ_81280030e9f37e4a3b34ce838e41b58feca51483 -Dsonar.projectName=to-do-app \
                   -Dsonar.sources=. \
                   -Dsonar.projectKey=to-do-app '''
               }
            }
           
		stage('OWASP Dependency Check') {
            steps {
               dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'DP'
                    dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
     

         stage('Docker Build') {
            steps {
               script{
                   withDockerRegistry(credentialsId: 'affd8909-e248-4c9a-ac2a-fc05a84eea5a') {
                    sh "docker build -t  todoapp:latest -f backend/Dockerfile ."
                    sh "docker tag todoapp:latest kahafsameer/todoapp:latest "
                    sh "docker push  kahafsameer/todoapp:latest "
                }
               }
            }
        }

       
        stage('trivy') {
            steps {
               sh " trivy image kahafsameer/todoapp:latest "
            }
        }
		stage('Deploy to Docker') {
            steps {
               script{
                    withDockerRegistry(credentialsId: 'affd8909-e248-4c9a-ac2a-fc05a84eea5a') {
                    sh "docker run -d --name to-do-app -p 3000:3000 kahafsameer/todoapp:latest "
                 }
               }
            }
        }

    }
}
