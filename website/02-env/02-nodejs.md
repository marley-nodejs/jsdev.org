---
layout: page
title: Node Version Manager (NVM) installation in Ubuntu 20.04
description: Node Version Manager installation and usage
keywords: node.js, Node Version Manager
permalink: /env/nodejs/
---

# Node Version Manager (NVM) installation in Ubuntu 20.04

<br/>

### Install packages

    $ sudo apt-get update && sudo apt-get install -qq -y vim git curl net-tools

<!--

    $ sudo apt-get install -y node.js

-->

<br/>

### Install latest Node Version Manager (NVM)

    -- current version
    https://github.com/creationix/nvm/releases

<br/>

    -- installation

    $ LATEST_VERSION=$(curl --silent "https://api.github.com/repos/nvm-sh/nvm/releases/latest" | grep '"tag_name"' | sed -E 's/.*"([^"]+)".*/\1/')

    $ curl -o- https://raw.githubusercontent.com/creationix/nvm/${LATEST_VERSION}/install.sh | bash

<br/>

    $ export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
    [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

<br/>

    $ nvm --version
    0.36.0

<br/>

### Install latest Node.js LTS

    // install latest LTS
    $ nvm install --lts

    $ node --version
    v12.18.4

or

    -- show possible
    $ nvm ls-remote

    // (Latest LTS: Erbium)
    $ nvm install v12.18.4

    $ nvm use v12.18.4

    -- set default
    $ nvm alias default v12.18.4

    $ node --version
    v12.18.4

<br/>

### For fast switching

    $ {
      nvm install v12.18.4
      nvm use v12.18.4
      nvm alias default v12.18.4
    }

<br/>

    $ {
      nvm install v8.17.0
      nvm use v8.17.0
      nvm alias default v8.17.0
    }

<br/>

### Install latest NPM

    $ nvm install-latest-npm

    $ npm --version
    6.14.8

<br/>

### Possible additional configs

<br/>

**packages.json**

```
"engines": {
    "node": ">=12.13.1",
    "npm": ">=6.13.4"
  },

***
```

**.npmrc**

```
engine-strict=true
```

<br/>

### Check updates for node packages

    $ npm install -g npm-check-updates
    $ ncu -u
    $ npm install