# Critical Files for Caprover Deployment

These are the files that you need to make this work:

1. Dockerfile
2. .github/workflows/deploy.yml
3. captain-definition
4. default.conf

# Setup

## Github Action Setup

Go to settings -> Secrets and variables -> actions

Add the following secrets
`CAPROVER_SERVER` - The server url of your caprover instance. This must be in the format of `https://caprover.example.com`
`CAPROVER_NAME` - The name of the app you want to deploy to
`CAPROVER_KEY` - The key of the app you want to deploy to

### `CAPROVER_SERVER` Secret

1. Set up a caprover instance
2. Make sure you have a domain name pointing to the server
3. Take the domain name and set it as the `CAPROVER_SERVER` secret in the format of `https://caprover.example.com`

### `CAPROVER_NAME` Secret

1. Create a new app
2. Set the app name to the same as the `CAPROVER_NAME` secret

### `CAPROVER_KEY` Secret

1. After creating the app, go to `Method 1: Official CLI`
2. Click `Enable App Token`
3. Take the token and set it as the `CAPROVER_KEY` secret

## Github Action Workflow

You can find the workflow file in `.github/workflows/deploy.yml`

## Dockerfile Setup

The docker file is located in `Dockerfile` and simply takes the built files from github's build and serves them on port 80
If the built files are not in `./dist` then you will need to change the `COPY` command in the dockerfile to match the location of your built files

## Troubleshooting

### Your built folder is not called `dist`

1. Go to `.github/workflows/deploy.yml` and change the `dist` to match the name of your built folder
2. Go to `Dockerfile` and change the `dist` to match the name of your built folder
