node {
    /*Docker Initialize*/
    stage('Initialize') {
        def dockerHome = tool 'Docker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }

    /*Building Test Environemnt*/ 
    stage('Building Test Environment') {
        /*Download new Docker Image from DockerHub*/
        withCredentials([usernamePassword( credentialsId: 'dockerhub-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials') {
                sh "docker login -u ${USERNAME} -p ${PASSWORD}"
                sh 'docker pull galloandreas/website:features'
            }
        }

        /*Stopping and removing previous Test Environments*/
        sh 'docker ps -f name=website:features -q | xargs --no-run-if-empty docker container stop'
        sh 'docker ps -f name=website:features -q | xargs --no-run-if-empty docker container rm'

        /*Starting new Test Environment*/
        sh  'docker run -d --name website:features -p 8000:8000 galloandreas/website'

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