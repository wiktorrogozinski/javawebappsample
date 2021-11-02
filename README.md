<h1>Azure and Jenkins</h1>
The project assumption was to host the app using the Azure App Service and simultaneously use Jenkins to deploy the app code. <br><br>
Tools which I have used:<br><br>
<b>1. GitHub</b> - necessary code was stored on GitHub. GitHub repository was connected with Jenkins. Every commit is built and deployed by Jenkins.<br><br>
<b>2. Azure</b> - I have used some azure functionalities. I have created a resource group. My resource group contains Virtual Machine which hosted Jenkins, App Service and App Service Plan. 
<br><br>

![azure_resource_group](https://user-images.githubusercontent.com/62955170/139865669-eee6be6f-9c51-4d8b-9026-eee42307c5bc.png)


<br><br><br>

<b>3. Jenkins</b> - I have created a Jenkins VM. I have prepared a machine to work by installing appropriate apps and functionalities. To configure JenkinsVM I have generated ssh key and connected to VM via SSH in the shell.  After creation VM I have connected to Jenkins via browser and configured it to work. I have installed azure credentials, Git and DSL plugin. I have added Azure service principal to Jenkins credentials -  the  "az ad sp create-for-rbac"  command was useful to do this. Then I have configured the Jenkinsfile with the proper name of resourceGroup, webAppName and credentialsId. My Jenkins Job is triggered by DSL script which starts the Jenkins job after committing to my GitHub repository.<br><br>
![Jenkins_Job](https://user-images.githubusercontent.com/62955170/139862987-b27f9724-3d1c-4867-b700-2fdeda8dfe84.png)
<br><br>
<b>App service</b> -Jenkins is responsible for delivering the latest app code to App service. The app service hosts the app and provides access to it.
 <br><br>

![app](https://user-images.githubusercontent.com/62955170/139864291-503ca79d-a31d-49de-9501-f759aff853d6.png)
