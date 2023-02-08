# adobe-app-builder-boilerplate

This is a project boilerplate for `aio` based apps for Adobe App Builder. You can use this repository
as a base for building your apps. It's also intended to serve as a home for our `.devcontainer` configuration
which can be launched on Github Codespaces as a developer sandbox, or as a local environment using vscode. 


## Working with Bitbucket

This repo contains some meta files for Bitbucket, a popular vcs platform used by many. While this repo intends to take
advantage of some github functionality, we still want our work to be compatible with Bitbucket and have this be a
natural starting point for agencies and enterprise teams leverging it. 

### Using This Template

Templates are useful because they don't bring with them old git histories. GitHub offers a green button to use a template, but 
if you wish to use this boilerplate on a bitbucket project, you can follow this procdure:

```bash
  git clone https://github.com/superterran/adobe-app-builder-boilerplate.git 
  cd adobe-app-builder-boilerplate
  rm -rf .git # deleting the .git directory removes git from the project, we just need to configure git for this project
  git init && git add . && git commit -m 'initial commit, from https://github.com/superterran/adobe-app-builder-boilerplate/tree/main'
  git push --set-upstream git@bitbucket.org:blueacorn/<repository-name>.git main
```

### Bitbucket Pipelines and Deployments

Bitbucket Projects can leverage the `bitbucket-pipelines.yml` file in this repository to provide a CI/CD suite. Currently, 
the pipeline performs an `aio app build` for all branches, and a `aio app deploy` for special branches `staging` and `main`.

| envvar                         | scope | description                                   |
| ------------------------------ |-------| --------------------------------------------- |
| AIO_runtime_apihost            | Repo-wide   | e.g.`https://adobeioruntime.net`            |
| AIO_runtime_auth               | Repo-wide   | auth value, [how to retrieve](https://developer.adobe.com/app-builder/docs/resources/ci-cd/lesson1/#github-secrets)   |
| AIO_WORKSPACE                  | Environment | String of workspace name, i.e.` Stage`      |
