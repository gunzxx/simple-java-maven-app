node {
    def mavenImage = docker.image('maven:3.9.0')
    mavenImage.inside('-v /root/.m2:/root/.m2') {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
