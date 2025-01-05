#creation_date:  2025-01-05 17:27
#modification_date: Sunday 5th January 2025 17:27:18
Error generating daily quote
#jenkins #ssh #git #github 

In command line of jenkins container we need
1. Register known hosts: use this command `git ls-remote -h git@github.com:Aleksei99/DEVOPS-jenkins-jobs.git HEAD`
2. Switch user to jenkins user: `su - jenkins`
3. go to `/var/jenkins_home/.ssh` create here private key that you use (id_ed25519)
4. paste data of private key `echo > id_ed25519 "----Begin .... ---END"`
5. `chmod 600 id_ed25519`