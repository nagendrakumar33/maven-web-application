node(){
    def gorilla = tool name: 'maven3.6.0', type: 'maven'
    stage('checkoutgit'){
    
    git changelog: false, credentialsId: '0b629644-ce76-4a0c-80f7-0ea3c755fda2', poll: false, url: 'https://github.com/nagendrakumar33/maven-web-application.git'
    }
    stage('checkoutmaven'){
        sh "${gorilla}/bin/mvn clean package"
    }
    stage('sonarqube report'){
        sh "${gorilla}/bin/mvn clean sonar:sonar"
    }
    stage('deploy to nexus'){
        sh "${gorilla}/bin/mvn clean deploy"
    }
    
    stage('tomcatdeploy'){
      sshagent(['nodecred']) {
 sh "scp -o StrictHostkeyChecking=no target/*.war ec2-user@13.233.96.154:/opt/apache-tomcat-9.0.20/webapps/maven-web-application.war"
}  
        
    }
}
    
    
    

    
    
    
    
    
    
    
    
    
    
    
