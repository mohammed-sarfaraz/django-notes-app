@Library("Shared") _
pipeline{
    
    agent { label "master" }
    
    stages{
        stage("Shared-library-testing"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
                script{
                    clone("https://github.com/LondheShubham153/django-notes-app.git", "main")
                }
            }
        }
        
        stage("build"){
            steps{
               script{
                   docker_build("notes-app","latest", "mohammed380")
               }
            }
        }
        
        stage("test"){
            steps{
                echo "This is testing the code"
            }
        }
        
        stage("push to docker hub"){
            steps{
                script{
                    docker_push("notes-app","latest","mohammed380")
                }
            }
        }
        
        stage("deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
                
            }
        }
    }
}
