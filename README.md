# AzureDotNetBuild.Ado
Use this Azure template to build your .NET Core projects. Build your .NET Core project either by running the dotnet build command in your pipeline or by using the .NET Core task.

## Pipeline Requirements

The dotNet Module pipeline requires the following parameters to be defined:

Parameters:

| Name  | Displayname | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | :-------------: | :-------------: | :-------------: | :-------------: | ------------- |
| projects | Path to project(s) | String |  |  | Optional | Specifies Path to project(s) |
| buildConfiguration | Configuration | String | release | test/release | Required | Specifies Configuration to pack |
| workingDirectory | Working directory | String |  |  | Optional | Specifies Working directory |

These parameters provide multiple use case options for the dotnet templates pipeline, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/AzureDotNetBuild.Ado
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: DotNet_Build.yaml
    parameters:
      projects: '${{ parameters.projects }}'                         
      buildConfiguration: '${{ parameters.buildConfiguration }}'
      workingDirectory: '${{ parameters.workingDirectory }}'

  ```
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.
