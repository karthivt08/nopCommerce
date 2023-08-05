pipeline {

agent any
options {
timeout(time: 1, unit: 'HOURS')

}
triggers { pollSCM('*/2 * * * *') }

parameters { 
    booleanParam(name: 'DEBUG_BUILD', defaultValue: true, description: 'Need to archive the Build') }

environment {
    dotnet = "/usr/lib/dotnet/sdk"
}

stages {

    stage ('code checkout') {
        steps {
            git branch: 'develop',
    url: 'https://github.com/karthivt08/nopCommerce.git'
        }
    }
    stage ('Restore stage') {

        steps {
            // for rc build
            
           sh 'dotnet restore src/NopCommerce.sln'
        }
    }

    stage ('Build stage') {

        steps {
            // for rc build
            
           sh 'dotnet -c Release build src/NopCommerce.sln'
        }
    }

    stage ('archive the files') {

        steps {
            sh 'dotnet public -c Release src/Presentation/Nop.web.csproj -o publish'
            sh 'mkdir publish/bin publish/logs'
            sh 'zip -r nopCommerce.zip publish'
            
        }

    }


}


}