node {
    def app

    stage('Clone repository') {
        /* repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* To builds the dockerimage */
        //update your ECR registry URI
        app = docker.build("https://676082793719.dkr.ecr.ap-northeast-2.amazonaws.com/myregi/demoapp")
    }

    stage('Test image') {
        /* Try killing some white walkers for testing ;-) */

        app.inside {
            sh 'echo "Hurray !! Tests passed, Valar Morghulis "'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image */
        //docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
        // update your ECR registry URI and jenkins crendential paramater
        docker.withRegistry('https://676082793719.dkr.ecr.ap-northeast-2.amazonaws.com/myregi', 'ecr:ap-northeast-2:aws_ecr')    {
            //app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
