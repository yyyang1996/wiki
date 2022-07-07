---
title: SSH
date: '2021-01-27T11:48:05.000Z'
icon: icon-style
background: bg-blue-400
tags:
  - protocol
  - remote
  - network
  - 22
categories:
  - Linux Command
intro: |
  This quick reference cheat sheet provides various for using SSH.
---

# ssh

## Getting started

### Connecting

Connect to a server (default port 22) \`\`\`shell script $ ssh root@192.168.1.5

````
Connect on a specific port
```shell script
$ ssh root@192.168.1.5 -p 6222
````

Connect via pem file (0400 permissions) \`\`\`shell script $ ssh -i /path/file.pem root@192.168.1.5

````
See: [SSH Permissions](/chmod#ssh-permissions)

### Executing
Executes remote command
```shell script
$ ssh root@192.168.1.5 'ls -l'
````

Invoke a local script \`\`\`shell script $ ssh root@192.168.1.5 bash < script.sh

````
Compresses and downloads from a server
```shell script {.wrap}
$ ssh root@192.168.1.5 "tar cvzf - ~/source" > output.tgz
````

### SCP

Copies from remote to local \`\`\`shell script $ scp user@server:/dir/file.ext dest/

````
Copies between two servers
```shell script
$ scp user@server:/file user@server:/dir
````

Copies from local to remote \`\`\`shell script $ scp dest/file.ext user@server:/dir

````
Copies a whole folder
```shell script
$ scp -r user@server:/dir dest/
````

Copies all files from a folder \`\`\`shell script $ scp user@server:/dir/\* dest/

````
Copies from a server folder to the current folder
```shell script
$ scp user@server:/dir/* .
````

### Config location

| File Path                | Description          |
| ------------------------ | -------------------- |
| `/etc/ssh/ssh_config`    | System-wide config   |
| `~/.ssh/config`          | User-specific config |
| `~/.ssh/id_{type}`       | Private key          |
| `~/.ssh/id_{type}.pub`   | Public key           |
| `~/.ssh/known_hosts`     | Logged in host       |
| `~/.ssh/authorized_keys` | Authorized login key |

### SCP Options

| Options       | Description                         |
| ------------- | ----------------------------------- |
| scp `-r`      | Recursively copy entire directories |
| scp `-C`      | Compresses data                     |
| scp `-v`      | Prints verbose info                 |
| scp `-P` 8080 | Uses a specific Port                |
| scp `-B`      | Batch mode _(Prevents password)_    |
| scp `-p`      | Preserves times and modes           |

### Config sample

```
Host server1 
    HostName 192.168.1.5
    User root
    Port 22
    IdentityFile ~/.ssh/server1.key
```

Launch by alias \`\`\`shell script $ ssh server1

````
See: Full [Config Options](https://linux.die.net/man/5/ssh_config)



### ProxyJump

```shell script
$ ssh -J proxy_host1 remote_host2
````

\`\`\`shell script {.wrap} $ ssh -J user@proxy\_host1 user@remote\_host2

````
Multiple jumps
```shell script {.wrap}
$ ssh -J user@proxy_host1:port1,user@proxy_host2:port2 user@remote_host3
````

### ssh-copy-id

\`\`\`shell script {.wrap} $ ssh-copy-id user@server

````
Copy to alias server
```shell script {.wrap}
$ ssh-copy-id server1
````

Copy specific key \`\`\`shell script {.wrap} $ ssh-copy-id -i \~/.ssh/id\_rsa.pub user@server

````
SSH keygen {.cols-5}
---------------

### ssh-keygen {.col-span-2}

```shell script
$ ssh-keygen -t rsa -b 4096 -C "your@mail.com"
````

| - | -    | -                              |
| - | ---- | ------------------------------ |
|   | `-t` | [Type](ssh.md#key-type) of key |
|   | `-b` | The number of bits in the key  |
|   | `-C` | Provides a new comment         |

Generate an RSA 4096 bit key with email as a comment

### Generate

Generate a key interactively \`\`\`shell script $ ssh-keygen

````
Specify filename
```shell script
$ ssh-keygen -f ~/.ssh/filename
````

Generate public key from private key \`\`\`shell script $ ssh-keygen -y -f private.key > public.pub

````
Change comment
```shell script
$ ssh-keygen -c -f ~/.ssh/id_rsa
````

Change private key passphrase \`\`\`shell script $ ssh-keygen -p -f \~/.ssh/id\_rsa

````
### Key type

- rsa
- ed25519
- dsa
- ecdsa



### known_hosts {.col-span-2}

Search from known_hosts
```shell script
$ ssh-keygen -F <ip/hostname>
````

Remove from known\_hosts&#x20;

```shell
$ ssh-keygen -R <ip/hostname>
```

### Key format

* PEM
* PKCS8

## See also

* [OpenSSH Config File Examples](https://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/) _(cyberciti.biz)_
* [ssh\_config](https://linux.die.net/man/5/ssh\_config) _(linux.die.net)_
