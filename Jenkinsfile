pipeline{
	agent any
stages{
	stage("Git Clone"){
	steps{
	git 'https://github.com/AhmedAtefGaber/discourse_docker/'
		}
			}
	stage("Docker Build"){
	steps{
	dir('image/base') {
    	sh "docker build  -t ahmedatefosman/discourse ."
			}
			}
				}
	stage("Docker Push"){
	steps{	
	withCredentials([string(credentialsId: 'docker_pass', variable: 'docker_pass')]) {
		sh "docker login -u ahmedatefosman -p ${docker_pass} "
					}
		sh "docker push ahmedatefosman/discourse"
			
			}
				}
/*
	stage("Deploy on kubernetes as deplyment and access the app from the service"){
	steps{
	sh "kubectl apply -f k8s/"
		      }	
				}

*/
	}	


}
