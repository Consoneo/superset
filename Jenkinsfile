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
                    sh label: "Install dependencies", script: "npm ci"
                }
            }
        }
        // stage("Run unit tests"){
        //     steps{
        //         dir("superset-frontend"){
        //             sh label: "Execute tests", script: "npm run test -- test packages"
        //         }
        //     }
        // }
        // stage("Lint"){
        //     steps {
        //         dir("superset-frontend"){
        //             sh label: "Prettier lint", script: "npm run lint"
        //         }
        //     }
        // }
        stage("Docker"){
            steps {
                container("dind"){
                    sh label: "Docker build", script: "docker build --target lean -t consoneo/superset:latest --build-arg PY_VER='3.8.12' . -m 3g --platform linux/amd64"
                }
            }
        }

    }
}
