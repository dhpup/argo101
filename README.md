# Hands-On

### 1. Fork The Example Repo

* Open https://github.com/dhpup/argo101
* Click “Fork”. 

### 2. Next Open the Argo CD UI & Add your application YAML.

* Open [Insert Argo CD UI URL here]
* Click + New App (Top Left)
* Application Name: Your GitHub Username
* Project: Default
* Sync Policy: Manual
* Source Repo: Paste the link to your forked repo.
* Source Path: In the dropdown select nginx/env/stage
* Destination: https://kubernetes.default.svc
* Namespace: default

### 3. Sync the application
* In the Argo CD UI click into your application. Then click the Sync button on the top bar.

### 4. In our CI steps, we're going to update the image version.
* Click into the GitHub Actions YAML file here: [GitHub Actions CI Steps](.github/workflows/gha.yml)
* Adjust the env version to 1.21.622
* Commit changes
* Sync the changes

### 5. Troubleshooting the deployment.





[GitHub Actions CI Steps](.github/workflows/gha.yml)

[Staging Environment Kustomization](nginx/env/stage/kustomization.yaml)

```
example code
```
