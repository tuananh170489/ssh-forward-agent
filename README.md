# How to configure SSH Forward Agent on Linux
### On local machine (MacOS/Linux/MS LinuxSubsystem)
Check ssh-agent status
```
eval "$(ssh-agent)"
```
If not running, start it
```
ssh-agent
```
Generate ssh key
```
ssh-keygen -t rsa -C 'example.com'
```
Add ssh key to agent
```
ssh-add -K ~/.ssh/id_rsa
```
Or add following line into ssh config
```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
  ForwardAgent yes
  ```
SSH to remote server using command
```
ssh -A user@server
```
### On remote server
On remote server, ssh to another server using command
```
ssh user@server
```
