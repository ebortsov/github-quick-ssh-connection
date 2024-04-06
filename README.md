# github-quick-ssh-connection
I often forget how to connect git and github with ssh, so I made this very short guide

# Quick connection to github
1. Check if folder `~/.ssh` exists. Delete all files in this folder if this folder exists.
2. `$ ssh-keygen -t ed25519 -C "your_github_email@email.com"` - generates a pair of ssh keys (the one with `.pub` extension is public key, the other is private key). They will be stored in `~/.ssh`.
If `ed25519` is not installed on the system, use another encryption algorithm. For example: `$ ssh-keygen -t rsa -b 4096 -C "your_github_email@email.com"`.
3. Copy public key to the clipboard (command works only on windows): `$ clip < .ssh/id_ed25519.pub`.
4. Add the public key to github in the settings.
5. Check connection: `$ ssh git@github.com`. 
6. `$ git remote add origin %SSH_URL_TO_REPO%`. `origin` is just the name (alias) of the main repository.
7. Check if repositories are indeed connected. `$ git remote -v`.
8. First push. `git push -u origin main`. (In the next pushes `$ git push` will work).
