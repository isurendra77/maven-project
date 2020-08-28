// Powered by Infostretch 

pipeline {
    agent any

timestamps {

node () {

	stage ('package_1 - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/isurendra77/maven-project']]]) 
	}
	stage ('package_1 - Build') {
 			// Maven build step
	withMaven(maven: 'localmaven') { 
 			if(isUnix()) {
 				sh "mvn clean package " 
			} else { 
 				bat "mvn clean package " 
			} 
 		} 
	}
	stage ('deploy-to-staging - Build') {
 	
// Unable to convert a build step referring to "hudson.plugins.copyartifact.CopyArtifact". Please verify and convert manually if required. 
	}
}
}
}