pipeline {
  // agent any
  agent {label 'slave'} //check specific working agent, becuase other agents stuck 
  stages {
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
''', description: 'Type of action to perform')
  }
}
