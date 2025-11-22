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

                xcopy /E /I /Y "%WORKSPACE%\\College-Website-master\\College\\*" "C:\\Program Files\\Apache Software Foundation\\Tomcat 11.0\\webapps\\ROOT\\"
                """
            }
        }

        stage('Restart Tomcat') {
            steps {
                bat """
                echo Restarting Tomcat...

                "C:\\Program Files\\Apache Software Foundation\\Tomcat 11.0\\bin\\shutdown.bat"
                timeout /t 5
                "C:\\Program Files\\Apache Software Foundation\\Tomcat 11.0\\bin\\startup.bat"
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

