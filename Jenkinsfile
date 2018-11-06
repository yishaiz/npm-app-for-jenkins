pipeline {
  // agent any
  agent {label 'slave'} //check specific working agent, becuase other agents stuck 
  stages {

    stage('Test') {
      when {
        expression {
          params.REQUESTED_ACTION == 'Test'
        }
    }
      steps {
        sh '''npm i
        npm test
        '''
      }
    }
 
    stage('Build Node App') {
      when {
        expression {
          params.REQUESTED_ACTION == 'Build'
        }
      }
      steps {
        sh '''npm i
        npm build
        '''
      }
    }

    stage('Deploy to Slave') {
      when {
        expression {
          params.REQUESTED_ACTION == 'Deploy'
        }
      }
      steps {
        sh '''mkdir playbooks/files
        cp nodejs-demoapp.zip playbooks/files/nodejs-demoapp.zip
        ansible-playbook deploy/deploy_dev.yml
        '''
      }
    }

  }
  parameters {
    choice(name: 'REQUESTED_ACTION', choices: '''Build
    Test
    Stage
    Deploy
''', description: 'Type of action to perform')
  }
 
}
