node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("emilijakostova/kiii-jenkins")
    }

    stage('Push image') {
        docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
