---
title: Anchor核心笔记
date: 2024-10-02 09:14:12
categories: [ 'Solana' ]
tags: [ 'Anchor' ]
---

> Anchor 工具资源：
> - [Install avm using Cargo. ] `~ % cargo install --git https://github.com/coral-xyz/anchor avm --locked --force`
> - [avm install latest fails？] `~ % cargo install --git https://github.com/coral-xyz/anchor --tag v0.30.1 anchor-cli --force`

> Last login: Wed Oct 16 00:29:07 on ttys000
hf@BENZCAR projects % anchor --version
anchor-cli 0.30.1
hf@BENZCAR projects % anchor init first-test-anchor
yarn install v1.22.22
warning ../../../../package.json: No license field
info No lockfile found.
[1/4] 🔍  Resolving packages...
warning mocha > glob@7.2.0: Glob versions prior to v9 are no longer supported
warning mocha > glob > inflight@1.0.6: This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Saved lockfile.
✨  Done in 27.28s.
Initialized empty Git repository in /Users/hf/Desktop/#Labs@Solana/projects/first-test-anchor/.git/
first-test-anchor initialized
hf@BENZCAR projects % 
