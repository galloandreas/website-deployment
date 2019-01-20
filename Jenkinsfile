node {
    /*Docker Initialize*/
    stage('Initialize') {
        def dockerHome = tool 'Docker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }

    /*Building Test Environemnt*/
    stage('Building Test Environment') {
        script {
            withDockerRegistry('https://registry.hub.docker.com', 'dockerhub-credentials') {
                sh 'docker pull galloandreas/website:features)'
            }
        } 
    }

    /*Pushing image to repository*/
    /*stage('Push Image to Repository') {
        echo '..pushing to Docker Hub'
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }*/
}