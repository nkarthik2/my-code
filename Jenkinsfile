pipeline {
    //agent {
    //    node{
    //        label 'master'
    //    }
    //}
    agent any
    script {
      properties([
        parameters([
          string(name: 'VERSION_NUMBER', defaultValue: '', description: 'If you want to change the patch version enter this value, else defaults to BUILDS_ALL_TIME')
        ])
      ])
    }
    environment {
        majorVersion = 3
        minorVersion = 9
        patchVersion = VersionNumber (versionNumberString: '${BUILDS_ALL_TIME}',overrideBuildsAllTime : '${params.VERSION_NUMBER}')
        //GITHUB_REPO_NAME = sh (returnStdout: true, script: "echo ${GIT_URL} | grep -Eo '[^/]+/?\$' | cut -d / -f1").trim()
        // GITHUB_STATUS_API_ENDPOINT = sh(returnStdout: true, script: "echo https://api.github.com/repos/picarro/${GITHUB_REPO_NAME}/statuses/${GIT_COMMIT}").trim()
    }
    stages {
	    stage ("Echo patchVersion") {
		  steps {
		    script {
			  echo "$patchVersion"
			  echo "Output of overrideBuildsAllTime"
			  echo "${env.overrideBuildsAllTime}"
		    }
		  }
		}
    }
    post {
	    success {
		  echo "It is success"
		}
    }
}
