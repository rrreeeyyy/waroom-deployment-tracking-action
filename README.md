This repository archived, use https://github.com/topotal/waroom-deployment-tracking-action instead.

# Waroom Deployment Tracking Action

This GitHub Action calls the Waroom Deployment Tracking API.
This allows you to track the status of deployments in Waroom.

## Usage

1. Create a new YAML file in the `.github/workflows` directory of your repository.
1. Configure the Action as follows:

```yaml
name: Waroom Deployment Tracking
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Waroom Deployment Tracking
      uses: topotal/waroom-deployment-tracking-action@v1
      with:
        organization: 'your-waroom-organization'
        service: 'your-waroom-service'
        key: ${{ secrets.WAROOM_DEPLOYMENT_INTEGRATION_KEY }}
        environment: 'production'
```

## Inputs

- `organization`: The Waroom organization name (required).
- `service`: The Waroom service name (required).
- `key`: The Waroom Deployment Integration Key (required)
  - Recommended to retrieve it from GitHub Secrets.
- `ref`: Ref for the deployment
  - default: `${{ github.sha }}`.
- `environment`: The environment where the deployment is taking place.
- `platform`: Platform of the repository
  - default: `github`
- `description`: Description for the deployments.
- `repository_owner`: Owner of the repository
  - default: `${{ github.repository_owner }}`
- `repository_name`: Name of the repository
  - default: `${{ github.event.repository.name }}`.
- `fail_on_error`: Fail the action if an error occurs
  - default: `false`
