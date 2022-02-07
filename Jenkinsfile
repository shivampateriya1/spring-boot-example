pipeline{
    agent any
    tools { 
        maven 'maven3'
    }
    stages
       {
            stage("clean")
            {
                steps{
                    sh "mvn clean"
                }
            }
            stage("Build")
            {
                steps{
                    sh "mvn compile"
                }
                
            }
            stage("TEST")
            {
                steps{
                    sh "mvn test"
                }
            } 
            stage("Package and Deplpy")
            {
                steps{
                    sh "mvn package"
            
                }
            }


        }
         post {
        always{
            mail to: 'shivam.pateriya@knoldus.com',
			subject: "Pipeline info",
			body: "you are build is ${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}"
        }
         success {
            echo "Packaging successful"
        }
        failure {
            echo "Packaging unsuccessful"
        }
    }
}        
    
	
    

