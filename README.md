To reproduce correct ansible playbook`s work you need to follow these steps:
1. Create new ssh-key with running command: 
> shh-keygen -t rsa -f ~/.ssh/mykey -N 'server'
2. Copy your ssh key to server:
> ssh-copy-id -i ~/.ssh/mykey user@host
3. Add to hosts file your server IP, username, and the path to the key
4. For one user we create a secret password and you need to put your value into the file
> nano vars/vault.yml<br/>
> vault_pass: [replace this with your value]
5. To encrypt your file run:
> ansible-vault encrypt vars/vault.yml
6. To run ansible playbook:
> ansible-playbook --connection=local main.yml --ask-vault-pass

## Note: 
Sometimes you need to add your key to ssh-agent, so run this:
> eval $(ssh-agent -s)<br/>
> ssh-add mykey

