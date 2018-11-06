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

  }
  parameters {
    choice(name: 'REQUESTED_ACTION', choices: '''Build
     Test
''', description: 'Type of action to perform')
  }
}
