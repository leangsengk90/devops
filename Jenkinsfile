pipeline{
  agent any

  stages{
    stage("Get Resources"){
      steps{
        sh """
          ansible-playbook -i ansible/inventory.ini ansible/playbooks/git.yml
        """
      }
    }
    stage("Build Project"){
      steps{
        sh """
          ansible-playbook -i ansible/inventory.ini ansible/playbooks/build.yml
        """
      }
    }
    stage("Docker Stage"){
      steps{
        sh """
          ansible-playbook -i ansible/inventory.ini ansible/playbooks/docker.yml
        """
      }
    }
  }
}
