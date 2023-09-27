pipeline {
    agent any
    parameters {
        choice(name: 'environment', choices: getEnvironmentChoices(env.BRANCH_NAME), description: 'Select the deployment environment')
    }
    stages {
        // Your pipeline stages go here
    }
}

def getEnvironmentChoices(branchName) {
    if (branchName.startsWith('master/')) {
        return 'Dev\nTest\nStaging\nProduction'
    } else if (branchName.startsWith('dev/')) {
        return 'Test\nStaging'
    } else {
        return 'Staging\nProduction'
    }
}
