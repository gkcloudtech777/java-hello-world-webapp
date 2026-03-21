pipeline{
   agent any
   tools {
        maven 'maven3.9'
        
    }
   
   stages{
       
     stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
     stage('Checkout stage'){
        steps{
           git 'https://github.com/gkcloudtech777/java-hello-world-webapp.git'
}
}
   stage('Build-stage'){
        steps{
            sh 'mvn clean package'
            sh 'mv target/*.war target/demo.war'
}
}
   stage("deploy war file"){
    steps{
          sshagent(['slave-id']) {
          sh "scp -o StrictHostKeyChecking=no target/demo.war jenkins@172.31.4.75:/var/lib/tomcat10/webapps"
                     }
                    }
                  }

}
}
