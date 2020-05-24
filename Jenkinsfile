pipeline {
	agent {
		label "master"
	}
	environment {
	  CDD_API_KEY = credentials('CDD_API_KEY')
	  CDD_APPLICATION_NAME = "${env.GIT_URL}"
	  CDD_APPLICATION_VERSION_NAME = "${env.GIT_BRANCH}"
	  CDD_GIT_COMMIT_ID = "${env.GIT_COMMIT}"
	  CDD_PREVIOUS_GIT_COMMIT_ID = "${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}"
	  CDD_SERVER_NAME = "lvntest002908.bpc.broadcom.net"
	  CDD_SERVER_PORT = "8080"
	  CDD_TEANANT_ID = "00000000-0000-0000-0000-000000000000"
	  CDD_USE_SSL = "false"
	  GIT_BRANCH = "${env.GIT_BRANCH}"
	  BRANCH_NAME = "${env.BRANCH_NAME}"
	  GIT_LOCAL_BRANCH = "${env.GIT_LOCAL_BRANCH}"
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
		stage("S5") {
			steps {
				echo '**** Build ****'
			}
		}
	}
	post {
		success {
			echo '----------Sending Build Notification to CDD--------------'
			echo "Environment variables: GIT_BRANCH: [$GIT_BRANCH], BRANCH_NAME: [$BRANCH_NAME], GIT_LOCAL_BRANCH: [$GIT_LOCAL_BRANCH]"
			sendNotificationToCDD useSourceCodeRepositoryNameAsApplicationName: true,
			appName: "${CDD_APPLICATION_NAME}",
			useSourceCodeRepositoryBranchNameAsApplicationVersionName: true,
			appVersion: "${CDD_APPLICATION_VERSION_NAME}",
			gitCommit: "${CDD_GIT_COMMIT_ID}",
			gitPrevSuccessfulCommit: "${CDD_PREVIOUS_GIT_COMMIT_ID}" ,
			overrideCDDConfig: [
				customApiKey: "${CDD_API_KEY}",
				customProxyPassword: '',
				customProxyUrl: '',
				customProxyUsername: '',
				customServerName: "${CDD_SERVER_NAME}",
				customServerPort: "${CDD_SERVER_PORT}",
				customTenantId: "${CDD_TEANANT_ID}",
				customUseSSL: "${CDD_USE_SSL}"
			],
			releaseTokens: '{}',
			ignoreNonexistentApplication: true
			echo '----------CloudBees Jenkins Pipeline completed successfully--------------'
		}
	}
}     
