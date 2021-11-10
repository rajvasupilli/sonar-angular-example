pipeline {
  agent any
  stages {
    stage('Build Parameters') {
      steps {
        script {
          properties([
            parameters([			
              choice(
                choices: ['myResourceGroup1', '${RESOURCE_GROUP}'],
                name: 'RESOURCE_GROUP'
              ),
              choice(
                choices: ['westus1', 'westus2'],
                name: 'LOCATION'
              ),
              choice(
                choices: ['myAppServicePlan1', 'myAppServicePlan2'],
                name: 'WEB_APP_PLAN_NAME'
              ),
              choice(
                choices: ['app1', 'app2'],
                name: 'WEB_APP_NAME'
              ),
              choice(
                choices: ['myACRName.azurecr.io/calculator:v1', 'myACRName.azurecr.io/calculator:v2'],
                name: 'DEPLOYMENT_CONTAINER_IMAGE'
              )
            ])
          ])
        }
      }
    }
    stage('Build') {
      steps {
        sh '''
              ng build
          '''
      }
    }

    stage('Deploy to Azure App Service') {
      steps {
        sh '''
          echo "Deploy"
          #az group create --name ${params.RESOURCE_GROUP} --location ${params.LOCATION}
				  #az acr create --name myACRName --resource-group ${params.RESOURCE_GROUP} --sku Basic --admin-enabled true
				  #az appservice plan create --name ${params.WEB_APP_PLAN_NAME} --resource-group  ${params.RESOURCE_GROUP} --is-linux
				  #az webapp create --resource-group ${params.RESOURCE_GROUP} --plan ${params.WEB_APP_PLAN_NAME} --name ${params.WEB_APP_NAME} --deployment-container-image-name ${params.DEPLOYMENT_CONTAINER_IMAGE}
        '''
      }
    }

  }
}
