# Hexo Deploy GitHub Pages Action

This GitHub action for building and deploying Hexo project to GitHub pages.

## Getting Started

You can view an example of this below.

```yml
name: Hexo Deploy GitHub Pages
on:
  push:
    branches:
      - hexo
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout
      uses: actions/checkout@hexo

    - name: Build and Deploy
      uses: ZhangWentao-PersonalGithub/ZhangWentao-PersonalGithub.github.io@hexo-deploy-github-pages-action
      env:
        PERSONAL_TOKEN: ${{ secrets.GITHUB_TOKEN }}

        # The repository the action should deploy to.
        PUBLISH_REPOSITORY: ZhangWentao-PersonalGithub/ZhangWentao-PersonalGithub.github.io

        # The branch the action should deploy to.
        BRANCH: hexo
```

if you want to make the workflow only triggers on push events to specific branches, you can like this: 

```yml
on:
  push:	
    branches:	
      - hexo
```

## Configuration

The `env` portion of the workflow **must** be configured before the action will work. You can add these in the `env` section found in the examples above. Any `secrets` must be referenced using the bracket syntax and stored in the GitHub repositories `Settings/Secrets` menu. You can learn more about setting environment variables with GitHub actions [here](https://help.github.com/en/articles/workflow-syntax-for-github-actions#jobsjob_idstepsenv).

Below you'll find a description of what each option does.

| Key                  | Value Information                                                                                                                                                                                                                                                                                                         | Type | Default | Required |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |---------| ------------- |
| `PERSONAL_TOKEN`     | Depending on the repository permissions you may need to provide the action with a GitHub Personal Access Token in order to deploy. You can [learn more about how to generate one here](https://help.github.com/en/articles/creating-a-personal-access-token-for-the-command-line). **This should be stored as a secret**. | `secrets` |         | **Yes** |
| `PUBLISH_REPOSITORY` | The repository the action should deploy to. for example `ZhangWentao-PersonalGithub/ZhangWentao-PersonalGithub.github.io`                                                                                                                                                                                                                                                 | `env` |         | **Yes** |
| `BRANCH`             | The branch the action should deploy to. for example `hexo`                                                                                                                                                                                                                                                              | `env` | `hexo` | **Yes** |
| `PUBLISH_DIR`        | The folder the action should deploy. for example `./public`                                                                                                                                                                                                                                                               | `env` | `./public` | No |
| `CNAME`              | The domain name of your GitHub Pages specified in a CNAME                                                                                                                                                                                                                                                                      | `env` |         | No |

