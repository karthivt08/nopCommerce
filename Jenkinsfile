pipeline {

agent any
options {
timeout(time: 1, unit: 'HOURS')

}

parameters { 
    booleanParam(name: 'DEBUG_BUILD', defaultValue: true, description: 'Need to archive the Build') }

   triggers {
        cron('1/30 * * * *')
    }
stages {

    stage ('code checkout') {
        steps {
            git branch: 'master',
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