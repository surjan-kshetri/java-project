properties([pipelineTriggers([githubPush()])])
node('linux') {
    
    stage ("GetInstances") {

        sh "aws ec2 describe-instances --region us-east-1"
    }

    stage("CreateInstance") {
        sh "aws ec2 run-instances --image-id ami-467ca739 --count 1 --instance-type t2.micro --key-name SEIS665-03 demo --security-group-ids sg-0fc84e78 --region us-east-1"
       
    }
       
}
