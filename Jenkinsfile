pipeline{
    agent{
        kubernetes {
            yamlFile  '.jenkins/podTemplate.yaml'
        }
    }
    stages{
        stage("Retrieve npm dependencies"){
            steps{
                dir("superset-frontend"){
                    container("node"){
                        sh label: "Install dependencies", script: "npm ci"
                    }
                }
            }
        }
        stage("Run unit tests"){
            steps{
                dir("superset-frontend"){
                    container("node"){
                        sh label: "Execute tests", script: "npm run test -- test packages"
                    }
                }
            }
        }
        stage("Build packages"){
            steps{
                dir("superset-frontend"){
                    container("node"){
                        sh label: "Build packages", script: "npm run test -- test packages"
                    }
                }
            }
        }

    }
}
