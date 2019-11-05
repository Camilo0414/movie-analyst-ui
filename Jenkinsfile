// This shows a simple example of how to archive the build output artifacts.
node {
    stage("clean"){
    cleanWs()
    }

    stage("checkout"){
        git branch: 'master', url: 'https://github.com/Camilo0414/movie-analyst-ui.git'
    }

    stage("build"){
        sh 'export BACK_HOST=training-i-lb-6a958bc843ae35f5.elb.us-east-2.amazonaws.com'
        sh 'npm install'
    }

    stage("deploy"){

        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/frontend/ ec2-user@10.0.1.161:/home/ec2-user/backend'
        sh 'ssh -i /var/jenkins_home/.ssh/id_rsa ec2-user@10.0.1.161 forever start /home/ec2-user/frontend/server.js'

        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/frontend/ ec2-user@10.0.4.165:/home/ec2-user/backend'
        sh 'ssh -i /var/jenkins_home/.ssh/id_rsa ec2-user@10.0.4.165 forever start /home/ec2-user/frontend/server.js'


    }
}
