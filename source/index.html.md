---
title: Rocky Stack

language_tabs:
  - code

toc_footers:
  - <a href='https://www.patreon.com/user?u=2517498'>Support On Patreon with $1 </a>


includes:
  - http
  - views
  - database
  - orm
  - security

search: true
---

# Introduction
## React Over Crystal, Kemal, & Yarn
Current version is ```1.1.0```

### Welcome to the ROCKY Stack
I built this as an experiment to put together the best libraries to build a modern yet simple stack.

I chose to base my stack

 * React - Solid front end framework backed by Facebook

 * Crystal - A powerful new language with syntax similar to ruby but is as fast as "C"

 * Kemal - Super light weight http framework made by Serdar Doğruyol

 * Yarn - The fastest package manager also made by Facebook

## Installation
Follow the code on the right for the installation commands that you will have to run on your operating systems terminal / console.

Requirements

### Rocky Project
```shell
git clone https://github.com/codingphasedotcom/rocky
```

Download or clone the ROCKY Project

[https://github.com/codingphasedotcom/rocky](https://github.com/codingphasedotcom/rocky)

homebrew for mac

## OS X (Mac)
```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Homebrew

```shell
brew update
brew install crystal-lang
brew install yarn
```

Make sure you have homebrew

## Ubuntu / Linux
```shell
curl https://dist.crystal-lang.org/apt/setup.sh | sudo bash
sudo apt-get install crystal
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```

Debian / Ubuntu

For other OSes and distros check the official documentation.

[https://yarnpkg.com/en/docs/install#linux-tab](https://yarnpkg.com/en/docs/install#linux-tab)




## Dependencies
### Get Crystal Dependencies
```shell
#terminal
shards install
```

Get all the "Backend" crystal dependencies


### Get Yarn Dependencies
```shell
#terminal
yarn install
```

Get all the "Frontend" dependencies


### Get Gulp
```shell
npm install --global gulp-cli
```

Install Gulp to be your task runner.

## Getting Started
```shell
#terminal
yarn run server
```

To test everything is good run the server.

Now if you visit ```http://localhost:3000/``` you should see the welcome home page

## Folders Structure


```html
#Folders
|-- .bowerrc
    |-- .jshintrc
    |-- .jshintrc2
    |-- Gruntfile.js
    |-- README.md
    |-- bower.json
    |-- karma.conf.js
    |-- package.json
    |-- app
        |-- app.js
        |-- db.js
        |-- directoryList.md
        |-- index.html
        |-- mddir.js
        |-- routing.js
        |-- server.js
        |-- _api
            |-- api.groups.js
            |-- api.posts.js
            |-- api.users.js
            |-- api.widgets.js
        |-- _components
            |-- directives
                |-- directives.module.js
                |-- vendor
                    |-- directive.draganddrop.js
            |-- helpers
                |-- helpers.module.js
                |-- proprietary
                    |-- factory.actionDispatcher.js
            |-- services
                |-- services.cardTemplates.js
                |-- services.cards.js
                |-- services.groups.js
                |-- services.posts.js
                |-- services.users.js
                |-- services.widgets.js
        |-- _mocks
            |-- mocks.groups.js
            |-- mocks.posts.js
            |-- mocks.users.js
            |-- mocks.widgets.js
```

This is an example not final
