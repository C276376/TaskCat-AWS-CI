pipeline {
    agent any
    stages{
        stage('Checkout Code'){
            steps{
                echo ( "Workspace = $WORKSPACE")
                git url: 'https://github.com/C276376/TaskCat-AWS-CI.git'
                sh "sleep 10s"
            }
        }
        stage('Runing taskcat')
        {
            steps
            {
                sh """
                        sleep 20s/
                        cd $WORKSPACE"/
                        taskcat -c ci/taskcat.yml/
                   """
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
