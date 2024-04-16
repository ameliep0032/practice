# Connecting VSCode and Github with SSH keys

## Generate SSH in VSCode
In VSCode:
- Open Git bash terminal at root level
- `ssh-keygen -t ed25519 -C "youremail@example.com"`
- When prompted to enter file, press enter
- When prompted to enter passphrase, press enter twice

## Copy SSH

- `cd ~/.ssh`
- `ls` to see the name of the files. You should see one similar to id_ed25519.pub
- `cat id_ed25519.pub` This will print the ssh key in the terminal
- Copy it to clipboard 

## Add SSH to Github

In Github website:
- Go to your settings
- Go to SSH and GPC Keys
- Click 'New SSH Key'
- Choose a name for your key
- Paste the ssh key you copied in the clipboard
- Click 'Add SSH Key'
- You should get a success banner and see your ssh key in the list now


## Test SSH connection

In Github website:
- Create empty repo in Github (no readme or gitignore)
- Copy the ssh url

In VSCode:
- Create folder in VSCode with `mkdir new-folder-name`
- `cd new-folder-name`
- `code .`

In this new VSCode window:
- Open a terminal
- `git init`
- Add remote origin (using ssh url from github) with: `git remote add origin {github-ssh-url}`

In Explorer menu on the left:
- Create a new file to repo: README.md, and add some dummy text to it
- Try to stage and commit changes. You should get a warning popup telling you that git username and password are not set yet.

In the terminal:
- Set your email with `git config --global user.email {your-github-email}`
- Set your username with `git config --global user.name {your-github-username}`

In the source control on the left:
- Commit your changes again (it should go through this time)
- Publish your branch

In Github website:
- Go to the repo, and you should see your README.md file and the dummy text that was added to it.