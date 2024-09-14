# testfox

trigger:
- main

pool:
  vmImage: ubuntu-latest

steps:
- task: NodeTool@0
  inputs:
    versionSpec: '14.x'
  displayName: 'Install Node.js'

- script: |
    npm install -g apifox-cli
    apifox run https://api.apifox.com/api/v1/projects/5164920/api-test/ci-config/459281/detail?token=xJtX3IKX1JWj6ovaSrhDwW -r html,cli  -b
  displayName: 'Install Apifox CLI and Run Tests'
