#!/usr/bin/groovy
node ('docker') {
    stage ('Building Image'){
        // run docker build job and push, make sure the directory is empty for
        // build
        build 'buildK8sBday'
        build 'cleanup'
        }
    
    stage ('Pushing to Staging - Kubernetes'){
        // build the kubernetes cluster
        build 'Staging-k8s'
        }
    stage ('Scale Testing'){
        // scale the deployment in kubernetes and rollback procedure
        build 'Staging-ScaleTest'
        }    
 //   stage ('Bundling'){
        //bundle the deployment to a yaml and helm chart
 //       build 'Bundling'
 //   }
    stage ('UAT'){
        //deploy to UAT for user acceptance testing using Helm chart
        build 'DeployUAT'
    }
    stage ('Deploy To Prod'){
        // create a helm chart from the repo and deploy
        build 'deployProd'
        } 
    }
