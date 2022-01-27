# SSH
---
_Required skills_
- Basic bash
- Basic git

_Required infrastructure_
- 2 ubuntu machines: one with SSH server on it, one with SSH client.

## Learning materials 
https://app.pluralsight.com/library/courses/ssh-telnet-protocol-deep-dive/table-of-contents 

https://www.youtube.com/watch?v=v45p_kJV9i4 

https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys

 

## Keywords 
- Symmetric/asymetric cryptography  
- Public-key cryptography 
- Public/private key 
- authorized_keys 
- Known_hosts
- sshd
- passhrase


## Commands 
- ssh 
- ssh-keygen 
- ssh-copy-id
- scp

## Questions 

1. What is SSH ?   Why do we need it? 
2. What is "known_hosts"  for what it is needed ?  
3. What is the “authorized_keys” file? What's the difference between this file and the “known_hosts” file?
4. What port is SSH server listening on?
5. How can you know if your machine can receive SSH connections?

## Exercises 

### Exercise 1 
1. Create a ssh key pair on your machine.
    - for simplicity - don't enter a passphrase
2. Given that you have the password to the server machine, do what is needed so you can login from your machine to the server without a password.
3. Use `scp` to clone some files from the HOME directory of the server to your machine.

### Exercise 2
Clone this `TrainingWorksheets` repository using the SSH url of it.