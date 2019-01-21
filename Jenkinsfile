node {
    /*Docker Initialize*/
    stage('Initialize') {
        def dockerHome = tool 'Docker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }

    /*Building Test Environemnt*/ 
    stage('Building Test Environment') {
        withCredentials([usernamePassword( credentialsId: 'dockerhub-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
            docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                sh "docker login -u ${USERNAME} -p ${PASSWORD}"
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