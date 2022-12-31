# Dockerizing a Node.js web app using Azure YAML Pipelines

In the part of this guide we will build a Docker image for the Node.js Web app , then we will instantiate a container from that image.

Main Objective of this process to deploy the web app using Azure YAML pipelines with enabling continuous deployment when there are changes in the source code.

Note: I already have the code of the app in the git hub repository.

<h2>Getting Started:</h2>
First the Azure Services used in this project are
<ul>
<li>Azure Registry Container to use it as a repository for the dockerized image from the docker file.</li>
<li>Azure WebApp for container to instantiate that image from ACR.</li>
</ul>

<h2>Process:</h2>
<h4>Create YAML Pipeline for Azure registry container</h4>
<u1>
<li>In the Azure devops create & run a yaml pipeline , here I have used github yaml pipeline to create Azure registry container so that it will fetch the templates & parameters from my git repo.</li>
  <img src="Screenshots/Pipeline for ACR.png" height="400" width="800">
</u1>
<h4>Create YAML Pipeline for Building image & WEB APP for container</h4>
<u1>
<li>create & run another yaml pipeline to build & Push a dockerized image to the container registry using the docker file from the repo.</li>
<li>Then add another stage to create web app for containers to host the image from the ACR. I have deployed 2 stage environments(staging & production)</li>
  <img src="Screenshots/Pipeline for Webapp.png" height="400" width="800">
</u1>
<h2>Result:</h2>
<li>Created Yaml Pipelines will be auto stored in git repo as we chose GitHub Yaml in the first place to create pipelines</li>
<img src="Screenshots/Yaml Pipelines in github.png" height="400" width="800">
<li>Resource Created in Azure portal after running the Yaml Pipelines</li>
<img src="Screenshots/Resources created in Azure Portal.png" height="400" width="800">
<li>WebApp Before Changes made in the Source Code</li>
<img src="Screenshots/Webapp before.png" height="400" width="800">
<li>WebApp After changes made in the source code as we have enabled trigger for Continuous deployment</li>
<img src="Screenshots/Webapp after.png" height="400" width="800">
