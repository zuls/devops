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
        sh 'docker login -u "zularbine" -p "MacBookPro321"'
        sh 'docker build -t zularbine/react-app:1 --no-cache .'
        sh 'docker push zularbine/react-app:1'
        sh 'docker rmi -f react-app zularbine/react-app:1'
      }
    }
  }
  catch (err) {
    throw err
  }
}