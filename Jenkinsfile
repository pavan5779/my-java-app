pipeline {
  agent { label 'my-agent' }  // Using the specified agent name
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/pavan5779/my-java-app.git'  // Your repository URL
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean package'  // Using Maven to build your application
      }
    }
    stage('Deploy') {
      steps {
        // Path to the PEM file and the deployment command
        sh 'scp -i "/var/lib/jenkins/workspace/Task-1/pradeep.pem" target/my-java-app.jar ubuntu@ec2-34-216-141-239.us-west-2.compute.amazonaws.com:/home/ubuntu'  // SCP command to copy the JAR file
        sh 'ssh -i "/var/lib/jenkins/workspace/Task-1/pradeep.pem" ubuntu@ec2-34-216-141-239.us-west-2.compute.amazonaws.com "java -jar /home/ubuntu/my-java-app.jar &"'  // SSH command to run the JAR file
      }
    }
  }
}
