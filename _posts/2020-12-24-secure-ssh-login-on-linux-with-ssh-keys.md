---
layout: post
title: "Secure SSH Login on Linux with SSH keys"
date: 2020-12-24 20:00:00 +0300
categories: technology development ssh
author: Anas Najaa
---

![Secure SSH Login on Linux with SSH keys](https://najaa-files.s3.me-south-1.amazonaws.com/blog/2024/08/0cf907e6-ea42-4b2b-8c5e-9e127f32e709.png)

This is a brief summary of the steps required to create a secure SSH login using public-private keys on Linux server.
A reference to the full guide can be found here:
[DigitalOcean SSH Setup Guide](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server)

## Requirements:

-   Linux server
-   Terminal using Bash

## Configuring the client

**1- Generate public/private keys on the client:**

```bash
ssh-keygen -t rsa
```

You can press enter for all prompts provided by the setup wizard.

**2- Copy the private key to your server:**

```bash
ssh-copy-id user@server-ip-address
```

> Note: In this step you need to specify the user which this key will be associated with. You'll be prompted to enter the login password for this user as well.

**3- You are ready to use the key to login:**

```bash
ssh user@server
```

## Disabling Password Authentication

**1- Login to your server:**

```bash
ssh user@server
```

**2- Edit SSH Daemon's configuration file:**

```bash
sudo nano /etc/ssh/sshd_config
```

**3- Search for the line that starts with `PasswordAuthentication` and uncomment it if it is commented and change it to:**

`PasswordAuthentication no`

**4- Restart SSH service to apply changes:**

```bash
sudo service ssh restart
```
