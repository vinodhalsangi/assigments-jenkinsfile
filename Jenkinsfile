pipeline {
  agent {
    label {
      label "built-in"
      customWorkspace "/mnt/jenkins-job"
    }
  }
  stages {
    stage ("clean ws") {
      steps {
        sh "sudo rm -rf *"
      }
    }
    stage ("httpd install") {
      steps {
        sh "sudo yum install httpd -y"
      }
    }
    stage ("permission") {
      steps {
        sh "sudo chmod -R 777 /var/www/html/"
      }
    }
    stage ("clean old build") {
      steps {
        sh "sudo rm -rf /var/www/html/*"
      }
    }
    stage {
      (Checkout SCM) 
      steps {
        dir ("/mnt/jenkins-slave") {
          sh "sudo cp index.html /var/www/html/"
        }
      }
    }
    stage ("start service") {
      steps {
        sh "sudo service httpd start"
      }
    }
    stage ("access permission") {
      steps {
        sh "sudo chmod -R 777 /var/www/html/"
      }
    }
  }
}
