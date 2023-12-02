pipeline {
	agent any

	stages {
		stage('SCM Checkout') {
			steps {
				git branch: 'main', url: 'https://github.com/vaisak1992/go-demo-cal.git'
			}
		}

		stage('Test') {
			steps {
				sh 'go test -v .'
			}
		}

		stage('Build') {
			steps {
				sh 'go build -v -o scalc -ldflags "-s -w"'
			}
		}

		stage('zip') {
			steps {
				sh 'zip --junk-paths scalc ./scalc'
			}
		}

		stage('Archive artifacts') {
			steps {
				archiveArtifacts artifacts: 'scalc.zip', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
			}
		}
	}
}
