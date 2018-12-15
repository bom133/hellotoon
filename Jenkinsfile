node {
    //def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
	     sh "docker build -t bom133/hellonode ."
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        //app.inside {
            sh 'echo "Tests passed"'
        }
    }

    //stage('Push image') {
    //    /* Finally, we'll push the image with two tags:
    //     * First, the incremental build number from Jenkins
    //     * Second, the 'latest' tag.
    //     * Pushing multiple tags is cheap, as all the layers are reused. */
    //    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
    //        app.push("${env.BUILD_NUMBER}")
    //        app.push("latest")
    //    }
    //}
    stage("Docker push") {
    //        environment {
    //            NEXUS_CREDS = credentials('nexus-login')
    //        }
            steps {
                // sh "echo $NEXUS_CREDS"
                // sh "echo $NEXUS_CREDS_USR"
                // sh "echo $NEXUS_CREDS_PSW"
                sh "docker login -u bom133 -p P@ssw0rd3"
                sh "docker push bom133/hellonode"

            }
    }

}
