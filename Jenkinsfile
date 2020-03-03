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
			withCredentials([string(credentialsId: 'CDD-Project-Mobile', variable: 'API-KEY')]){
	                	sh 'echo  $API-KEY'
			}
		}
		success { 
			sendNotificationToCDD appName: 'Mobile-GUI', 
					appVersion:  "${env.BRANCH_NAME}", 
					gitCommit: "${env.GIT_COMMIT}",
					gitPrevSuccessfulCommit: "${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}",
					overrideCDDConfig: [
							customApiKey: 'eyJhbGciOiJIUzUxMiJ9.eyJ1c2VybmFtZSI6InN1cGVydXNlckBjYS5jb20iLCJ0ZW5hbnRJZCI6IjAwMDAwMDAwLTAwMDAtMDAwMC0wMDAwLTAwMDAwMDAwMDAwMCIsInVzZXJJZCI6MSwianRpIjoiOTUzYzFiNmQtMWYzZS00NTJiLTk1NTQtNGUwMzM5ZGU5OTI5IiwiZXhwIjoxNTkxMDI1MDM4fQ.Z4Vec7LTLfO5glp9olmn7F8R2B08VlwKc8Dh-1zeWG6EnMASEGnYYWTBXjswVFEtnoNRZyrogIm1jzqfN8eb0Q',
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
