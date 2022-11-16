# API Sample: Order tracking
## Automation

This git repo contains a sample API to use with API Connect.  If you want to try API Connect, you can sign up for a [free 30 day trial](https://register.automation.ibm.com/apic/trial/aws?source=github_sample) and import this API.


This document will guide you through the sample CI/CD setup within this git repo to automate publishing your API definitions to API Connect when the source files in GitHub change.  In this example we're using GitHub Actions, but the same steps would be portable to any CI/CD toolchain. 



## Step by step guide:

1. Clone this repo into your own github account. 


2. Add repository secrets so the action can access your API Connect instance
    - Retrieve an API Key from your API Connect instance by visiting `/manager/sign-in/?from=TOOLKIT` on your API Connect instance and logging in - you can use these links for APIC on AWS: [us-east](https://api-manager.us-east-a.apiconnect.automation.ibm.com/manager/sign-in/?from=TOOLKIT)
    - Click on Settings on your cloned repo, and then Secrets, Actions from the navigation.
    - Create a secret called APIKEY and set the value to the API Key provided in API Manager.
    - Update `.github/workflows/deploy-api.yml` with the details of your API Connect instance - particularly the provider org and catalog names.

3. Update the API in your repo and commit the change 
    - open orders_api.yaml in your cloned repo and click Edit
    - Make a change to the file - maybe change the title?
    - Commit the changes to the repo with the 'Commit changes' button, optionally providing a description of the change

4. View the GitHub Action workflow
    - Click 'Actions' from the tabs at the top of your repo
    - You should see the workflows for Deploy API and Validate API and a list of workflow runs
