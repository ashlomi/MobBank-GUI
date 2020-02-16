pipeline {
    agent {
        label "master"
	}
    stages {
        stage("Export Porject") {
            steps {
             echo '**** mvn Build****'
			}
        }
        stage("Zip Project") {
            steps {
                echo '**** mvn Build****'    
            }
        }
        stage("Publish to Nexus") {
            steps {
			  echo "*** nexusVersion*****"       
			}
		}
	}		
    post { 
		always { 
			echo '----------Sending Build Notification to CDD--------------'
		}
		success { 
			sendNotificationToCDD appName: 'MobBank-GUI', 
					appVersion:  "${env.BRANCH_NAME}", 
					gitCommit: "${env.GIT_COMMIT}",
					gitPrevSuccessfulCommit: "${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}",
					overrideCDDConfig: [
							customApiKey: 'eyJhbGciOiJIUzUxMiJ9.eyJ1c2VybmFtZSI6InN1cGVydXNlckBjYS5jb20iLCJ0ZW5hbnRJZCI6IjAwMDAwMDAwLTAwMDAtMDAwMC0wMDAwLTAwMDAwMDAwMDAwMCIsInVzZXJJZCI6MSwianRpIjoiMGE4MjllNTUtYjFiMy00ZWQ4LTgwYTYtNTFjNmUzYzQ3OTNmIiwiZXhwIjoxNTg5NjQ4Mjg4fQ.mrTaJD-gPLODJ518AFyWK1Iixy3krWuvNOMD2WwVIJlxKE-wgNo56Z5rtnZQjFAPTf6HBde5mPCnZxNXS3ohhg',
							customProxyPassword: '',
                            				customProxyUrl: '',
                           				customProxyUsername: '',
                            				customServerName: 'lvntest002908.bpc.broadcom.net',
                            				customServerPort: 8080,
                            				customTenantId: '00000000-0000-0000-0000-000000000000',
                            				customUseSSL: false
                    			],
					releaseTokens: '{}'
		}
	}
}
