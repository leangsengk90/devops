pipeline{
  agent any
  // environment {
  //   PATH="/usr/bin:$PATH"
  //   LC_ALL = 'en_US.UTF-8'
  //   LANG = 'en_US.UTF-8'
  // }
  stages{
    stage("Get Resources"){
      steps{
        sh """
          ansible-playbook -i ansible/inventory.ini -l workers ansible/playbooks/git.yml
        """
      }
    }
    stage("Build Project"){
      steps{
        sh """
          ansible-playbook -i ansible/inventory.ini -l workers ansible/playbooks/build.yml
        """
      }
    }
    stage("Docker Stage"){
      steps{
        sh """
          ansible-playbook -i ansible/inventory.ini -l workers ansible/playbooks/docker.yml
        """
      }
    }
  }
}
