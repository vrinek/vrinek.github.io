---
layout: post
title: "Good enough JS development environment on OSX"
date: 2015-12-21 20:39:49
---

I recently started working on a small web-app to learn React. First thing on my TODO was to set up a development environment and since we live in the age of containers, I restricted myself to only use Docker. Bad news is I'm on OSX.

## Step zero - some background

Docker on OSX is a little problematic. This is because it depends on Linux-specific features and thus it has to run within a VM with OSX as the host. This leads to a few problems:

* slightly larger memory usage (not a biggie)
* inodes getting exhausted which is manifested as "No space left on device" which is really annoying
* filesystem watches don't propagate properly

This last part was the one I eventually managed to solve in a "good enough" manner.

In any case, I installed the [Docker Toolbox](https://www.docker.com/docker-toolbox) and after a `docker-machine create --driver virtualbox default` I had a VM to put containers in. `eval (docker-machine env default)` set up all the environment variables that made the `docker` command line interface work.

## Step one - pulling containers

Before that gets into the picture though, `docker pull node`.

Upon doing that, I hit upon the "No space left on device" error. Classic solution, turn off and on again: `docker-machine restart default`. Then `docker pull node` again. This time it worked for me.

## Step two - skeleton app

The skeleton application can be inspected at https://github.com/vrinek/one-budget/tree/good-enough. It's only 6 short files so I assume it's easy to browse through. Most of the boilerplate code was pulled straight out of [Egghead's React lessons](https://egghead.io/technologies/react).

## Step three - building, running

    docker build -t kostas/one-budget .; and docker run -it -p 3333:3333 -v (pwd)/src:/app/src kostas/one-budget

Now `open http://(docker-machine ip default):3333/webpack-dev-server/index.html` should get you a nice "Hello" and little more. If you update the `src/App.js` file and save it, you should see the browser update immediately.

## The small detail

There's one small detail that turned this from "well, at least it works" to "good enough" for real development.

Assuming that a volume has been mounted (`-v` option on the `docker run` command), the filesystem changes should be propagated from OSX to the VM and from the VM to the Docker container. Sadly that OSX to VM part is kinda broken (as mentioned on step zero).

Others have tried [setting up rsync linked up to a watcher](https://github.com/brikis98/docker-osx-dev) to circumvent this problem (inspired by that I tried using btsync which I had already installed). I tried a few of those but as usual, the more the moving parts, the greater the chance it won't work. In the end, a more primitive approach solved this issue.

    // from webpack.config.js:11
    watchOptions: {
      poll: true
    }

This will simply [poll the filesystem for changes](http://webpack.github.io/docs/webpack-dev-middleware.html#lazy). It's not fast and it's not sexy but it's "good enough" to get some serious work done with React on Docker on OSX.

Cheers!

## Note to non-fish users

["Fish"](http://fishshell.com) is my shell of choice and it has a slightly different syntax to bash. To translate the above shell snippets to bash simply replace `; and` with `&&` and prepend any parenthesis `(interpolation)` with a dollar sign `$(interpolation)`. Alternatively, install fish, it's awesome!
