---
created-at: 
tags:
- How-To
- Git
date: 2024-02-27
summary: A simple guide to setting up paswordless CLI Git operations when working with Github
title: How to Setup Github SSH
categories:
lastMod: 2024-02-28
---
# Some Context...
---

Github has deprecated using account passwords for authenticating Git operations on [Github.com](https://github.com/) as written in [this](https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/) article. Now, if you're like me and use the CLI often, you'd realise that using a PAT (personal access token) gets cumbersome real quick. So here's a guide on how to use SSH keys for authenticating your Git operations to Github on the CLI.

This guide only covers the basic syntaxes and steps you need to do. Assuming that you could setup Git on your machine on your own or that you already have Git installed.

# Configuring `.gitconfig`
---

If you don't already have your `.gitconfig` file configured, here are a few things that is marginal to be inside your `.gitconfig` and some other nice-to-haves.



## `user.name` and `user.email`

Your username and email should be inside your `.gitconfig` file. For context, the username can be different from your Github username, but the email should be the same. Since the email is going to be used to create the `ssh-key` later on.
```
$ git config --global user.name "your username"
$ git config --global user.email "your.mail@mail.com"
```



## `init.defaultBranch`

After that, since Github changed the default branch name from `master` to `main`, you could also do that on your local machine with this command
```
$ git config --global init.defaultBranch main
```



## Other Configurations

The rest of the configuration you can look at the `man` page for `git-config` or check the online version [here](https://git-scm.com/docs/git-config). Here's the rest of my config in my machine
```
$ git config --global core.editor nvim  		# main text editor
$ git config --global color.ui auto				# colorful git
```

# Configuring Local SSH Key
---

After setting up the `.gitconfig` now We can continue to creating a local SSH-Key. Github uses the SSH key to authenticate any Git operations to your repository. 

Before anything, start by checking your local machine for an existing Ed25519 algorithm SSH key. Type this command to the terminal and check the output
```
$ cat ~/.ssh/id_ed25519.pub
```

If an error message saying "No such file or directory", that means there's no existing Ed25519 SSH key on your machine. If no such message appears, then you can continue to the next step.



## Creating SSH Key

To create an SSH key with the Ed25519 algorithm, run the following command 
```
$ ssh-keygen -t ed25519 -C "your.mail@mail.com"
```

> 💡
The `-C` flag is to write a comment, otherwise the key
 will be generated with your computer’s username. The convention is to 
use your email as a comment to indicate who generated the public key.

When a prompt appears asking you where to save the generated key, just press `Enter`.

Next, it will ask you for a password; enter one if you wish, if not just press `Enter`

# Linking Local SSH Key with Github
---

Now, We need to register our new SSH key with Github to enable passwordless authentication when accessing from the CLI.

First, sign in into [Github](https://github.com/), and then click on your profile picture on the top right corner. Navigate to the `Settings` in the drop down menu.

Next, on the left hand side, click `SSH and GPG Keys`. Then, click the green button on the top right corner that says `New SSH Key`. Give a distinct name to your key so that it is easy to remember. Leave this window open as you proceed to the next steps.

Now, copy the existing SSH key on your local machine by running the following command
```
 $ cat ~/.ssh/id_ed25519.pub
```

Highlight the output–which starts with `ssh-ed25519` and ends with your email–and copy it to your clipboard.

Now, go back to GitHub in your browser window and paste the key you copied into the key field. Keep the key type as `Authentication Key` and then, click `Add SSH key`. You’re done! You’ve successfully added your SSH key!

# Testing Your Key
---

To verify your SSH connection, you can follow [this article from Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection?platform=linux)
