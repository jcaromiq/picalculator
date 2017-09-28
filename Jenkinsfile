node {
    stage("scm") {
        git url: 'https://github.com/jcaromiq/picalculator'
    }
    stage("test and build") {
        sh "docker build -t jcaromiq/picalculator ."
    }
    stage("push") {
        withCredentials([[
            $class: 'UsernamePasswordMultiBinding', 
             credentialsId: 'docker_hub',
             usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD'
        ]]) {
            sh "docker login -u $USERNAME -p $PASSWORD"
            sh "docker push jcaromiq/picalculator"
        }
    }
}