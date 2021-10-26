pipeline {
    //agent {
    //    node{
    //        label 'master'
    //    }
    //}
    agent any
    parameters {
        string(name: 'VERSION_NUMBER', defaultValue: '', description: 'Enter a integer to override BUILDS_ALL_TIME, leave default value if you do not want to override')
    }
    environment {
        majorVersion = 3
        minorVersion = 9
        patchVersion = VersionNumber (versionNumberString: '${BUILDS_ALL_TIME}',overrideBuildsAllTime : '${VERSION_NUMBER}')
        //GITHUB_REPO_NAME = sh (returnStdout: true, script: "echo ${GIT_URL} | grep -Eo '[^/]+/?\$' | cut -d / -f1").trim()
        // GITHUB_STATUS_API_ENDPOINT = sh(returnStdout: true, script: "echo https://api.github.com/repos/picarro/${GITHUB_REPO_NAME}/statuses/${GIT_COMMIT}").trim()
    }
    stages {
	    stage ("Set Build name" ) {
	      steps {
	        script {
	          currentBuild.displayName = "$majorVersion" + "." + "$minorVersion" + "." + "$patchVersion";
	        }
	      }
	    }
	    stage ("Echo patchVersion") {
		  steps {
		    script {
			  echo "$patchVersion"
			  echo "Output of overrideBuildsAllTime"
			  echo "${env.overrideBuildsAllTime}"
			  echo "Params VERSION_NUMBER"
			  echo "${params.VERSION_NUMBER}"
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
