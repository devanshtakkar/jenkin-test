def fetchLatestVersion() {
    // Read the CHANGELOG.md content
    def changelogContent = readFile 'CHANGELOG.md'

    // Use regex to capture version numbers within square brackets.
    def matcher = (changelogContent =~ /##\s\[(\d+\.\d+\.\d+)\]/) 
    if (matcher) {
        // The first match should be the latest version if the changelog has the latest version at the top
        return matcher[0][1]
    } else {
        error "Failed to find a version in the CHANGELOG.md"
    }
}

pipeline {
    agent any

    stages {
        stage('Fetch Latest Version') {
            steps {
                script {
                    def latestVersion = fetchLatestVersion()
                    echo "Latest Version: ${latestVersion}"
                }
            }
        }
    }
}