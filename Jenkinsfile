node{
    
    currentBuild.displayName = "java-app-#"+currentBuild.number
    
    stage("Git Clone") {
        
        git url: 'https://github.com/abhishekkishor/java-web-app-jenkins-nexus.git', branch:'master'
        
    }
    
    stage("Maven Build"){
        
        sh "mvn clean package"
        
        archiveArtifacts artifacts: '**/*.war'
        
    }
    
    stage("Nexus Repo") {
        
        def readPom = readMavenPom file: 'pom.xml'
        
        nexusArtifactUploader artifacts: [
            [
                artifactId: 'simple-app',
                classifier: '',
                file: "target/simple-app-${readPom.version}.war",
                type: 'war'
            ]
        
        ],
                
        credentialsId: 'nexus3', 
        groupId: 'in.javahome', 
        nexusUrl: '172.31.8.152:8081', 
        nexusVersion: 'nexus3', 
        protocol: 'http', 
        repository: 'java-app',
        version: "${readPom.version}"
        
    }
    
}
