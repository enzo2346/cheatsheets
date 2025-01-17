On Windows:

### Generate new SSH key:

1. Open Git Bash

2. Paste the text below, replacing the email used in the example with your GitHub email address

```shell
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

3. Fill the fields required

### Add your SSH key to the ssh-agent

1. In a new admin elevated PowerShell window, ensure the ssh-agent is running:

```shell
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
```

```shell
Start-Service ssh-agent
```

2. In a terminal window without elevated permissions, add your SSH private key to the ssh-agent. 

```shell
ssh-add c:/Users/YOU/.ssh/id_ed25519
```

### Add a new SSH key to your account:

1. Copy the content of the file `c:/Users/YOU/.ssh/id_ed25519.pub` (your public key):

```shell
cat ~/.ssh/id_ed25519.pub | clip
```

2. Paste it on GitHub or on BitBucket