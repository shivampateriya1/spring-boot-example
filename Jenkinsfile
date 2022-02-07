pipeline{
    agent {
        label 'Master'
    }
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
                    sh "mvn clean test"
                }
            } 
        }
         post {
        always{
            mail to: 'shivam.pateriya@knoldus.com',
			subject: "Pipeline: ${currentBuild.fullDisplayName} is ${currentBuild.currentResult}",
			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
        }
         success {
            echo "Testing is successful"
        }
        failure {
            echo "Testing is failed"
        }
    }
    
}
