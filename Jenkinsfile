node {
    
    stage('Clone sources') {
        git url: 'https://github.com/dhiraj4191/spring-framework.git'
    }

    stage ('Analysis') {
        def mvnHome = tool 'maven'
 
        sh "${mvnHome}/bin/mvn -batch-mode -V -U -e checkstyle:checkstyle pmd:pmd pmd:cpd findbugs:findbugs"  

        step([$class: 'hudson.plugins.checkstyle.CheckStylePublisher', pattern: '**/target/checkstyle-result.xml', unstableTotalAll:'0',unhealthy:'100', healthy:'100'])
        step([$class: 'PmdPublisher', pattern: '**/target/pmd.xml'])
        step([$class: 'FindBugsPublisher', pattern: '**/findbugsXml.xml'])
    }
}