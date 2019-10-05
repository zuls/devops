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
        sh 'docker build -t 172.16.0.23:5000/react-app --no-cache .'
        sh 'docker push 172.16.0.23:5000/react-app'
        sh 'docker rmi -f react-app 172.16.0.23:5000/react-app'
      }
    }
  }
  catch (err) {
    throw err
  }
}