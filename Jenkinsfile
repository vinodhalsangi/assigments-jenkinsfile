pipeline {
  agent {
    label "built-in"
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
    stage ("deploy") {
      steps {
        sh "sudo cp index.html /var/www/html/"
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
