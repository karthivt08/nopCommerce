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

    stage ('archive the files') {

        steps {
            sh 'mkdir nopcommercepckg'
            sh 'cp -r /var/lib/jenkins/workspace/nopcommerce/src/Libraries nopcommercepckg'
            sh 'cp -r /var/lib/jenkins/workspace/nopcommerce/src/Presentation nopcommercepckg'
            sh 'zip -qr nopcommercepckg.zip nopcommercepckg'
        }

    }


}


}