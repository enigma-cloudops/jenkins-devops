node {
	stage('prepare') {
		git branch: 'main', poll: false, url: 'https://github.com/RiteshDevOpsTrainer/restro.git'
	}
	
	stage('build') {
		def mvnHome = tool 'MAVEN'
		withEnv(["MVN_HOME=$mvnHome"]){
			sh '"$MVN_HOME/bin/mvn" clean compile package'
		}
	}
	
	stage('deploy') {
		deploy adapters: [tomcat9(credentialsId: 'c7ba21e9-0018-4029-93aa-fdac97a3c3cb', path: '', url: 'http://13.233.86.137:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
	}

}
