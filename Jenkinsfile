pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Thiyanesh2002/College-Application.git'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat """
                echo Copying website files to Tomcat...

                xcopy /E /I /Y "%WORKSPACE%\\*" "C:\\Users\\thiyanesh\\OneDrive\\Desktop\\Jenkins\\College-Website-master\\webapps\\ROOT\\"
                """
            }
        }

        stage('Restart Tomcat') {
            steps {
                bat """
                echo Restarting Tomcat...

                C:\\Users\\thiyanesh\\OneDrive\\Desktop\\Jenkins\\College-Website-master\\bin\\shutdown.bat
                timeout /t 5
                C:\\Users\\thiyanesh\\OneDrive\\Desktop\\Jenkins\\College-Website-master\\bin\\startup.bat
                """
            }
        }
    }

    post {
        success {
            echo "Deployment completed successfully!"
        }
        failure {
            echo "Deployment failed!"
        }
    }
}
