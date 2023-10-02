pipeline {
    agent any
    parameters {
        choice(name: 'environment', choices: getEnvironmentChoices(env.BRANCH_NAME), description: 'Select the deployment environment')
    }
    stages {
        stage("Validate Choice")
        {
            steps{
                script{
                sh 'curl -s "${BUILD_URL}/api/json" | tr "{}" "\n" | grep "Started by")'
                echo " Printing build cause ${BUILD_CAUSE_JSON}"
                echo "Hey you have choosen ${params.environment}"
                }
            }
        }
        // Your pipeline stages go here
    }
}

def getEnvironmentChoices(branchName) {
    echo " printing branch name: ${env.BRANCH_NAME}"
    if (branchName == 'main') {
        return 'UAT\nProduction'
    } else if (branchName == 'dev') {
        return 'Test\nStaging'
    } else {
        return 'Sandbox\nSample'
    }
}

