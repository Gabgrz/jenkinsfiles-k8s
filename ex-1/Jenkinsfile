pipeline {
  agent {
    kubernetes {
        yaml: '''
        apiVersion: v1
        kind: Pod
        spec:
        containers:
        - name: docker
            image: docker:19.03.1-dind
            securityContext:
            privileged: true
            env:
            - name: DOCKER_TLS_CERTDIR
                value: ""
        - name: helm
            image: "dtzar/helm-kubectl:3.7.2"
            command:
            - cat
            ttyEnabled: true
        '''
    }
  }
  stages {
    stage('Check helm version') {
      steps {
        container('helm') {
          sh 'helm version'
        }
      }
    }
  }
}
