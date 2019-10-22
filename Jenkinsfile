// This shows a simple example of how to archive the build output artifacts.
node {
    stage("clean"){
    cleanWs()
    }

    stage("checkout"){
        git branch: 'master', url: 'https://github.com/Camilo0414/movie-analyst-ui.git'
    }

    //INSTALATION PREVIOUSLY MADE
    // stage("install"){
    //     sh 'curl -sL https://deb.nodesource.com/setup_10.x | bash -'
    //     sh 'apt-get install -y nodejs'
    // }

    stage("build"){
        sh 'export BACK_HOST=if-lb-training-5621dfd50c7b2cab.elb.us-east-2.amazonaws.com'
        sh 'npm install'
    }

    stage("deploy"){
        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/frontend/ ec2-user@10.0.1.116:/home/ec2-user/frontend'
        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/frontend/ ec2-user@10.0.4.5:/home/ec2-user/frontend'
    }
}