# ssh-private-key-buildpack

A Heroku buildpack for setting the ssh private key as part of the application build. 

## Setup

### 1. Add the buildpack to your app

In the Heroku Dashboard for your app, add this buildpack (the repo URL), and make sure it is first. 

### 2. Configure SSH Key

Set the private key environment variable `SSH_KEY` of your Heroku app (must be base64 encoded).

    $ heroku config:set SSH_KEY=$(cat path/to/your/keys/id_rsa | base64)

By default the buildback adds Github to `known_hosts`. However you can configure your app to allow custom hosts, too. 
All that's needed is the set `SSH_HOSTS` for you app to a comma-delimited list of hosts, e.g. `git@github.com,example.com`

    $ heroku config:set SSH_HOSTS="git@github.com,example.com"
