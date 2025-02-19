@Library("Shared") _

pipeline{
    
    agent {label "agent_2"}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                clone("https://github.com/Rishabh1404/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "rishabh143")
                }
            }
        }
        stage("Push to dockerhub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "rishabh143")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
