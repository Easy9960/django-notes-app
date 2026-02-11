@Library("Shared") _
pipeline{
    
    agent {label 'vinod'}
    
    stages{
        stage("Hello"){
          steps{
              script{
                  hello()
              }
          }
        }
        
        stage("code"){
            steps{
                script {
                 clone( 
                     "https://github.com/Easy9960/django-notes-app.git",
                      "main")
                  }
            }
        }
        stage("Build"){
            steps{
              script{
            docker_build("notes-app", "latest", "vinodkumar95")
           }
        }
    }
        stage("Push to DockerHUB"){
            steps{
             script{
               docker_push("notes-app", "latest", "vinodkumar95")
            }
          }
        }
        stage("Deploy"){
            steps{
            echo "This is Deploying code"
            sh "docker compose up -d"
            }
        }
    }
}
