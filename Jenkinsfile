pipeline {
  agent any
	tools {
		maven 'M2_HOME'
		}

  stages {
	stage('Deploy to repository') {
		  steps {
			sh "mvn clean package -U"
		        sh "mvn build-helper:parse-version versions:set -DnewVersion=\\\${parsedVersion.majorVersion}.\\\${parsedVersion.minorVersion}.\\\${parsedVersion.incrementalVersion}-build${env.BUILD_NUMBER} versions:commit"
		        sh "mvn clean install package"
		        echo 'Tagging version'
		        sh "mvn -Dusername= 'naveenkumar199901@gmail.com' scm:tag"
	  }
	}

  }
}
