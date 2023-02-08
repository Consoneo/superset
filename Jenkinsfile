pipeline{
    agent{
        kubernetes {
            yamlFile  '.jenkins/podTemplate.yaml'
            defaultContainer 'node' 
        }
    }
    stages{
        stage("Retrieve npm dependencies"){
            steps{
                dir("superset-frontend"){
                    sh label: "Install dependencies", script: "npm install && npm ci"
                }
            }
        }
        stage("Run unit tests"){
            steps{
                dir("superset-frontend"){
                    sh label: "Execute tests", script: "npm run test -- test packages"
                }
            }
        }
        stage("Build packages"){
            steps{
                dir("superset-frontend"){
                    sh label: "Build packages", script: "npm run plugins:build"
                }
            }
        }

    }
}
