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
							customApiKey: 'eyJhbGciOiJIUzUxMiJ9.eyJ1c2VybmFtZSI6InN1cGVydXNlckBjYS5jb20iLCJ0ZW5hbnRJZCI6IjAwMDAwMDAwLTAwMDAtMDAwMC0wMDAwLTAwMDAwMDAwMDAwMCIsInVzZXJJZCI6MSwianRpIjoiZGI1OGE4NGUtNGQ5ZC00YjQxLWI4ODQtMDA1M2MzODI2MjBlIiwiZXhwIjoxNTg5MzY3MjM0fQ.cBdHAqRUfVJ_RMjpJkiuxbYLdLrSstgxbclDgEwnbVZiqYbuwiekqclMbJPVoiwWu2nGnWLZ2_cBHPLew07dvQ',
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
