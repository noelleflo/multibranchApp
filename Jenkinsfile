pipeline {
	agent any 
		stages {
			stage('git-clone'){
				steps{
					checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'token', url: 'https://github.com/noelleflo/multibranchApp.git']]])
				}
			}
			stage('parallel-level'){
				parallel {
					stage('sub-job1'){
						steps{
							echo "sub-job1 task"
						}
					}
					stage('sub-job2'){
						steps{
							echo "sub-job2 task"
						}
					}
					stage('user checkout'){
						steps{
							sh 'cat /etc/passwd |grep jenkins'
						}
					}
				}
			}
			stage('version-check'){
				steps{
					echo "end of parallel job"
				}
			}
		}
}
