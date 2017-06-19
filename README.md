# how-to-npm
[![Build Status](https://travis-ci.org/workshopper/how-to-npm.svg?branch=master)](https://travis-ci.org/workshopper/how-to-npm)
[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/workshopper/how-to-npm?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](http://standardjs.com/)

A module to teach you how to module. This version has the advantage of working on Windows if you installed node to the default location (or to any location that has spaces in the path)

## Huh?

The upstream version of this package uses [which](https://github.com/npm/node-which) to find npm, and then passes the resolved location to child_process.exec(). The problem is, child_process.exec() ends up invoking the command interpreter with /s:
```
cmd.exe /s /c "C:\Program Files\nodejs\npm.cmd"
```
So the quotes that child_process adds are summarily ignored. Net result - if the path to npm has spaces, it looks like several arguments are being passed instead of a single path:
```
cmd.exe /s /c C:\Program Files\nodejs\npm.cmd
```

(We'll ignore for the moment that this is introduces a potential security flaw <3)

The workaround in this version is to wrap the output of which.sync() in another set of quotes, which will be preserved by cmd. As a result, I can't guarantee that this version works anywhere but on Windows, and in cmd.

## PREREQUISITES

To use this project, you'll need NodeJS. Visit http://www.nodejs.org to
download and learn more!

## USAGE

```
npm i -g how-to-npm
how-to-npm
```

![Workshopper screen](assets/images/Workshopper%20screen.png)

This will walk you through the basics of setting up a working
environment, installing dependencies, logging into npm, publishing a
module, and so on, all from the safety of your own laptop.

## OPEN OPEN SOURCE

This is an [open open source project]. Individuals making significant
and valuable contributions are given commit-access to the project to
contribute as they see fit.

[open open source project]: http://openopensource.org/
