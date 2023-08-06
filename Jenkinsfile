pipeline {

agent { label 'Node001' }
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
    stage ('Build Docker Image') {

        steps {
            // for rc build
            
           sh 'docker image build -t nopcommerce:${GIT_COMMIT} .'
        }
    }
stage ('Docker Image push') {

        steps {
            // for rc build
            
           sh 'docker image tag nopcommerce:${GIT_COMMIT} karthimaga/nopcommerce:${GIT_COMMIT}'
           sh 'docker image push karthimaga/nopcommerce:${GIT_COMMIT}'
        }
    }

}


}