pipeline {
    agent any
    stages{
        stage('Checkout Code'){
            steps{
                echo ( "Workspace = $WORKSPACE")
                git url: 'git@github.com:EliLillyCo/EIP_gdm_aws_sandbox_rds.git'
                sh "sleep 10s"
            }
        }
        stage('Initiating Taskcat') {
            steps{
                dir ("$WORKSPACE") {
                    sh ". $WORKSPACE/Invoketaskcat.sh;
                }
            }
        }
      
    
    }
    post {
        always {
            echo 'One way or another, I have finished'
        }
        success {
            mail body: "Build Success ${env.BUILD_URL}",
            cc: 'sharma_gaurav1@network.lilly.com',
            subject: "RDSBUILD : Success Pipeline: ${currentBuild.fullDisplayName}",
            to: 'sharma_gaurav@network.lilly.com'
        }
        unstable {
            echo 'I am unstable :/'
        }
        changed {
            echo 'Things were different before...'
        }
        failure {
            mail body: "Something is wrong with ${env.BUILD_URL}",
            cc: 'sharma_gaurav@network.lilly.com',
            subject: "RDSBUILD : Failed Pipeline: ${currentBuild.fullDisplayName}",
            to: 'sharma_gaurav@network.lilly.com'
        }
    }
}
