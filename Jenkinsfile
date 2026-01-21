@Library("shared") _
pipeline{   
    agent { label "agent-sh"}
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
                    clone("https://github.com/Shivam123shi/django-notes-app.git","main")
                }
            } 
        } 
        stage("Build"){
            steps{ 
                script{
                docker_build("notes-app","latest","shivam206" )
                }
            } 
        } 
        stage("Push to dockerHub"){
            steps{ 
                script{
                 docker_push("notes-app","latest","shivam206")   
                }
            } 
        } 
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d" 
                
            } 
            
        } 
        
    } 
    
}
