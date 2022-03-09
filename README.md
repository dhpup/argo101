# Hands-On

### 0. Prerequisites.
* A GitHub account.
* An Argo CD Instance. (If attending the Webinar we will provide one for you to use.)

### 1. Fork The Example Repo.
* Open https://github.com/dhpup/argo101
* Click “Fork”. 

### 2. In your forked Repo enable GitHub Actions. 
* Click "Actions" in the top bar at GitHub.com in your repo. 
* Enable GitHub Actions workflows to be executed.

### 3. In our CI steps, we're going to update the image version.
* Click into the GitHub Actions YAML file here: [GitHub Actions CI Steps](.github/workflows/gha.yml)
* Adjust the env version to 1.21.6
* Commit the changes on GitHub.
* Once the GitHub Actions build completes, you can verify the changes were made to your staging environment YAML here: [Staging Environment Kustomization](nginx/env/stage/kustomization.yaml)

### 4. Next Open the Argo CD UI & Add your application YAML.
* Open the Webinar Argo CD UI here: [Argo CD UI for Argo 101 Webinar](thisdoesntexistyet) | Or use your own Argo CD instance. 
* (You won't need to login if using the Webinar Argo CD instance provided.) Click "Login" in the top right then log in via GitHub.
* Click "+ New App" (Top Left), then configure the following settings.
> Application Name: Your GitHub Username \
 Project: Default \
 Sync Policy: Manual \
 Source Repo: Paste the link to your forked repo. (e.g. https://github.com/dhpup/argo101) \
 Source Path: In the dropdown select nginx/env/stage \
 Destination: https://kubernetes.default.svc \
 Namespace: default
* Click "Sync" in the Argo CD UI to deploy your application.

### 5. Deploy a new artifact version.
* Click into the GitHub Actions YAML file here: [GitHub Actions CI Steps](.github/workflows/gha.yml)
* Adjust the env version to 1.21.622
* Commit the changes to GitHub. 
* Wait for GitHub Action to complete.
* Argo CD will detect the drift. 
* Click "Sync" to deploy this new version.

### 6. Troubleshooting the deployment.
* Once you sync the new artifact, you will notice your application is in an unhealthy state. 
* Follow the red statuses on Argo CD and you can figure out why. 
* Click into the unhealthy pod then check the events and logs.
* Rollback the deployment.
