node{
    
    stage("Git Clone") {
        
        git url: 'https://github.com/abhishekkishor/java-web-app-jenkins-nexus.git', branch:'master'
        
    }
    
    stage("Maven Build"){
        
        sh "mvn clean package"
        
        archiveArtifacts artifacts: '**/*.war'
        
    }
    
    stage("Nexus Repo") {
        
        nexusArtifactUploader artifacts: [
            [
                artifactId: 'simple-app',
                classifier: '',
                file: 'target/simple-app-1.0.war',
                type: 'war'
            ]
        
        ],
                
        credentialsId: 'nexus3', 
        groupId: 'in.javahome', 
        nexusUrl: '13.214.151.217:8081', 
        nexusVersion: 'nexus3', 
        protocol: 'http', 
        repository: 'java-app',
        version: '1.0'
        
    }
    
}
