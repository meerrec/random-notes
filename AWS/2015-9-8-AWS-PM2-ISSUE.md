---
layout: post
title: Dealing with a wired issues for PM2 on AWS EC2!
category: Tools, Issue
tags: AWS, NODE, DEPLOY
---

## Issue

After installed `node.js` and `pm2` on AWS EC2, cannot run pm2!

## Reason

`pm2` tried to find excutable `node`. However, somehow `nodejs` is the right one instead `node`

## Solution

- Check where is the `node` installed

```
which node
/usr/sbin/node
```

- Check where is the `nodejs` installed

```
which nodejs
/usr/bin/nodejs
```


- Remove old `node`, and make a new link `node` to `nodejs`

```
sudo rm /usr/sbin/node
sudo ln -s /usr/bin/nodejs /usr/sbin/node
```

## Done!
