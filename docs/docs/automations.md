# Automations

A number of automations are available to facilitate the development, quality assurance, security, deployment, maintenance and onboarding of the service. Here we describe some that are directly, publicly available.

## Dockerfile

The main delivery package for the service is a docker image. The [Dockerfile](https://github.com/terra-horizon/terra-aai/blob/main/src/Dockerfile) bundled under the project repo for the service builds the Docker image.

## Docker image publishing

A GitHub Action workflow is available to [build and publish](https://github.com/terra-horizon/terra-aai/blob/main/.github/workflows/docker-publish.yml) the generated docker image for the service. The action is triggered when a new tag is created in the repository. This way, all the images produced are always named and can be traced back to the codebase snapshot that generated them.

The generated docker image is pushed to the GitHub organization Packages using the name of the service repo and the version tag that triggered the execution.

## Vulnerability Scanning

A GitHub Action workflow is available to [scan for vulnerabilities](https://github.com/terra-horizon/terra-aai/blob/main/.github/workflows/vulnerability-scan-on-demand.yml) any docker image that was created for the service. The action is triggered manually and expects as input the version tag that was used to generate the respective docker image that must be scanned.

Vulnerability scanning is performed using [Trivy](https://trivy.dev/). The results are generated in SARIF format and are made available in the GitHub Code Scanning tool that is configured for the service.

Trivy is utilized to scan both the configuration that triggers the Docker image generation (ie the Dockerfile) as well as the generated image. The scanning performed on the generated image includes both OS vulnerabilities as well as installed libraries.

## Static Code Analysis

A GitHub Action workflow is available to [analyze the code](https://github.com/terra-horizon/terra-aai/blob/main/.github/workflows/codeql-scan-on-demand.yml) using static code analysis offered through GitHub's CodeQL. The action is triggered manually and can be executed against the HEAD of the repository.

The scan is configured to evaluate rules on security, quality and maintenability of the codebase. The results generated are made available in the GitHub Code Scanning tool that is configured for the service.

## Testing

A GitHub Action workflow is available to [perform API smoke testing](https://github.com/terra-horizon/terra-aai/blob/main/.github/workflows/test-on-demand.yml) any configured installation of the service. The action is triggered manually and expects as input the version tag that contain the version of the tests that are compatible with the version of the deployed installation under test.

Smoke testing of the APIs is perfomed using a [Postman](https://www.postman.com/) collection of requests. Configuration that needs to be passed in a protected way is maintained as GitHub Secrets. The request collection is axecuted using the [Newman CLI](https://github.com/postmanlabs/newman). The output of the test run presents a summary of the requests performed and any errors that may have been observed.

## Documentation

A GitHub Action workflow is available to [generate documentation](https://github.com/terra-horizon/terra-aai/blob/main/.github/workflows/deploy-docs-on-demand.yml) available in the project in the format presented here. The action is triggered manually and can be executed against the head of the repository. The documentation generated is versioned and the documentation version is expected as input to the workflow. 

The documentation is build using the [mkdocs](https://www.mkdocs.org/) library and specifically using the [Material for mkdocs](https://squidfunk.github.io/mkdocs-material/) plugin. A number of additional tools are ustilized, such as [mike](https://github.com/jimporter/mike) to support versioning, and others.

The documentation is generated and tagged with the provided version. It is uploaded to a dedicated documentation branch that is configured to be used as the base branch over which the repository GitHub Page presents its contents.