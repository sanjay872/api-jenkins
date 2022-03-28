pipeline {
    agent any 
    stages {
        stage('Compile and Clean') { 
            steps {

                bat "mvn clean compile"
            }
        }
      
        stage('deploy') { 
            steps {
                bat "mvn package"
            }
        }
        
        stage('run app'){
        	script {
        		try{
        			bat "taskkill /FI "WindowTitle eq api*" /T /F"	
        		}
        		catch(error){
        			echo "vendor not running"
        		}
        		finally{
        				bat "start "api" java -jar target/api-jenkin-0.0.1-SNAPSHOT.jar"
        		}
        	}
        }
    }
}