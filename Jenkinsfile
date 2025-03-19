node{
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
    stages {
        stage('Clone Repository') {
          
                git branch: "dev" , url: "https://github.com/Pradeep-S07/sample-war.git"
            
        }

        stage('Build with Maven') {
                
                sh "/usr/share/maven/bin mvn package"
            
        }

        stage('Deploy to Tomcat') {
            steps {
                script {
                    def warFile = findFiles(glob: 'target/*.war')[0].path
                    echo "Deploying WAR file: ${warFile} to http://localhost:8010/new"

                    sh """
                        curl -u admin:admin123 \\
                        -T ${warFile} \\
                        "http://localhost:8000/manager/text/deploy?path=/britto&update=true"
                    """
                }
            }
        }
    }

    post {
        success {
            echo "Deployment successful! Access your app at: http://localhost:8010/new"
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
