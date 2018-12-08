properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Test') {    
		git 'https://github.com/surjan-kshetri/java-project.git'
		sh 'ant -f test.xml -v'
		junit 'reports/result.xml'
	}   
	stage('Build') {    
		sh 'ant -f build.xml -v'   
	}   
	stage('Deploy') {    
		junit 'https://s3.console.aws.amazon.com/s3/buckets/assignment10665/rectangle-2.jar'   
	}
	stage('reports') {
		junit 'sh "aws ec2 run-instances --image-id ami-467ca739 --count 1 --instance-type t2.micro --key-name SEIS665-03 demo --security-group-ids sg-0fc84e78 --region us-east-1"'
	}
}
