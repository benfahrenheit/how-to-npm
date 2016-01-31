# how-to-npm

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

## USAGE

```
npm i -g how-to-npm
how-to-npm
```

<img src="https://s3.amazonaws.com/f.cl.ly/items/0A0o3t012V0i1Y222p0E/Screen%20Shot%202015-02-07%20at%2023.20.50%20.png" alt="Workshopper screen">

This will walk you through the basics of setting up a working
environment, installing dependencies, logging into npm, publishing a
module, and so on, all from the safety of your own laptop.
