pipeline {
    //agent {
    //    node{
    //        label 'master'
    //    }
    //}
    agent any
    environment {
        majorVersion = 3
        minorVersion = 9
        patchVersion = VersionNumber (versionNumberString: '${BUILDS_ALL_TIME}',overrideBuildsAllTime : '$overrideBuildsAllTime')
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
