#creation_date:  2024-10-28 15:24
#modification_date: Monday 28th October 2024 15:24:23
Error generating daily quote

# Git config
#Git #config #auth #github

> [!DESCRIPTION] 
> How to use  multiple accounts with ssh and github
### .ssh/config 
```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/bank_rsa
  
Host github-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519
```

```bash
	git remote set-url origin git@github-personal:Aleksei99/obsidian.git
```