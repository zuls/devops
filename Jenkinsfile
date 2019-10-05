node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'docker -v'
      sh 'printenv'
    }

    stage('Deploy'){
      if(env.BRANCH_NAME == 'master'){
        sh 'docker build -t zularbine/react-app --no-cache .'
        sh 'docker push zularbine/react-app'
        sh 'docker rmi -f react-app zularbine/react-app'
      }
    }
  }
  catch (err) {
    throw err
  }
}