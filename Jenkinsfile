pipeline {
 
    agent = any
 
    stages {
        stage('Initial Notification') {
            steps {
                 //put webhook for your notification channel 
                 echo 'Pipeline Start Notification'
            }
        }
stage('Code Analysis') {           
            steps {
               //put your code scanner 
                echo 'Code Scanning and Analysis'
            }
        }
 
        stage('Robot Testing') {
            steps {
                //put your Testing
                echo 'Robot Testing Start'
            }
            post{
                success{
                    echo "Robot Testing Successfully"
                }
                failure{
                    echo "Robot Testing Failed"
                }
            }
        }
stage("Build"){
	 steps {
		echo "Docker Build"
		docker build -f Dockerfile -t pavanbolla/autodockerbuild:$BUILD_NUMBER .  
		docker login -u pavanbolla/autodockerbuild -p $DOCKER_PWD 
		docker push pavanbolla/autodockerbuild:$BUILD_NUMBER
             }
            post{
                success{
                    echo "Build and Push Successfully"
                }
                failure{
                    echo "Build and Push Failed"
                }
            }
        }
}
}