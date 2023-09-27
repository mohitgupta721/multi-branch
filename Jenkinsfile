pipeline {
    agent any
    parameters {
        choice(name: 'environment', choices: getEnvironmentChoices(env.BRANCH_NAME), description: 'Select the deployment environment')
    }
    stages {
        stage("First")
        {
            steps{
                echo "This is first stage of deployment"
            }
        }
        // Your pipeline stages go here
    }
}

def getEnvironmentChoices(branchName) {
    echo " printing branch name: ${env.BRANCH_NAME}"
    if (branchName.startsWith('main/')) {
        return 'Dev\nTest\nStaging\nProduction'
    } else if (branchName.startsWith('dev/')) {
        return 'Test\nStaging'
    } else {
        return 'Staging\nProduction'
    }
}
