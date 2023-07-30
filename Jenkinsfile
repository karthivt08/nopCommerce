pipeline {

agent any
options {
timeout(time: 1, unit: 'HOURS')

}

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

    stage ('Build stage') {

        steps {
            
           sh 'dotnet build src/NopCommerce.sln'
        }
    }
}


}