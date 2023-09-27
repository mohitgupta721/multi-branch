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
        echo "Printing from inside checj if cond for main branch"
        return 'Dev\nTest\nStaging\nProduction'
    } else if (branchName.startsWith('dev/')) {
        return 'Test\nStaging'
    } else {
        return 'Staging\nProduction'
    }
}
