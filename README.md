The project assumption was to host the app using the Azure App Service and simultaneously use Jenkins to deploy the app code. <br><br>
Tools which I have used:<br><br>
<b>1. GitHub</b> - there was stored the app code. Any change was pushed to GitHub. The GitHub was connected with Jenkins.<br><br>
<b>2. Azure</b> - I have used some azure functionalities. I have created a resource group. My resource group contains Virtual Machine which hosted Jenkins, App Service and App Service Plan. <br><br>
![resource_group](https://user-images.githubusercontent.com/62955170/139863077-9834d368-5f7b-4bcf-80c0-ae38faa2dc4d.png)
<br><br>

<b>3. Jenkins</b> - I have created a Jenkins VM. I have prepared a machine to work by installing appropriate apps and functionalities.  To configure JenkinsVM I have generated ssh key and connected it with the machine via SSH in the shell. After creation VM I have connected to Jenkins via browser and configured it to work. I have installed azure credentials, Git and DSL plugin. I have added Azure service principal to Jenkins credentials -  the  "az ad sp create-for-rbac"  command was useful to do this. Then I have configured the Jenkinsfile with the proper name of resourceGroup, webAppName and credentialsId. My Jenkins Job is triggered by DSL script which starts the Jenkins job after committing to my GitHub repository.<br><br>
![Jenkins_Job](https://user-images.githubusercontent.com/62955170/139862987-b27f9724-3d1c-4867-b700-2fdeda8dfe84.png)
<br><br>
<b>Azure Web app</b> - Jenkins is responsible for delivering the latest app code to Azure Web App. Azure Web App hosts the app and provides access to it.<br><br>
![app](https://user-images.githubusercontent.com/62955170/139862912-86ffb6bb-9633-46d2-b6f3-cffaccb63636.png)
