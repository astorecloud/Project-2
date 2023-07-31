pipeline 
{
    agent any

 //   stages 
    {   
         stage ('Stop Container') 
        {
            steps 
            {
               script{
                    sh 'docker stop project2'
                }
            }
        }
        
        stage ('Remove Container') 
        {
            steps 
            {
                script {
                    sh 'docker rm project2'
                }
            }
        }
         stage ('Remove Container Image') 
        {
            steps 
            {
                script {
                    sh 'docker rmi project2 '
                }
            }
  //      }
        stage ('Build docker image') 
        {
            steps 
            {
                script{
                    sh 'docker build -t project2 .'
                }
            }
        }
        stage('Build docker Container') 
        {
            steps 
            {
                script{
                    sh 'docker run -d --name project2 -p 8081:80 project2 '
                }
            }
        }
    }
    post 
    {   
        always
        {
            emailext body: 'Summary', subject: 'Pipeline status', to: 'ahsan@gmail.com'
        }

    }
}