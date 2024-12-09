# Setting up Ubuntu Workstation 

This repository contains basic steps and commands for easily seting up ubuntu workstation

## Installing Nodejs
### Install Nvm
1. Install Node Version Manager(NVM) but downloading it from the [Node Version Manager]( https://nodejs.org/en/download/package-manager/current ) official website.
2. Type ```curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash ``` and press ```<Enter> ```
3. Restart your machine. For Wsl2 close the Ubuntu application and then Reopen.
4. Type nvm and press ``<Enter>`` to verify installation is successful

### Install Nodejs
1. Type ``nvm install --lts `` and press ``<Enter>``
2. Type ``nvm list`` and press ``<Enter>`` to verify installation


## Python Installation

### I nstalling pyenv
1. Install pyenv using [pyenv-installer](https://github.com/pyenv/pyenv-installer) by running this command:
```bash
 curl https://pyenv.run | bash
```
2. Open your `.zshrc` or `.bashrc` file with the following command:
```bash
 code ~/.zshrc
```
or 
```bash
 code ~/.bashrc
```
3. Add the following lines
```
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
```
4. To get your startup file to execute, restart your terminal.

### Installing Dependencies on Ubuntu
1. First run this command to update your apt repositories:
```bash
 sudo apt update
```
2. Next, run this command to install the packages listed on the pyenv:
```bash
 sudo apt-get install -y build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git
 ```

### Installing Python
1. Run the following command to install Python (*Replace 3.8.13 with the python version you want to install*):
```bash
 pyenv install 3.8.13
```
After some time this should complete without any errors. It could take a while since you are compiling Python from source code.
2. Once this is finished we also need to tell pyenv this is our default version of Python using this command(*Replace 3.8.13 with the python version you want to be your default version*):
```bash
 pyenv global 3.8.13
```
3. Ensure that these changes take effect by closing your terminal and opening a new one.
4. Verify your installation by typing
```bash
 python --version
 python3 --version
```
Both of these commands should show 3.8.13

### Installing Pipenv 
1. Type this to install pipenv
```bash
pip install pipenv
```
2. After you have installed pipenv, modify your shell startup file (either `~/.bashrc` or `~/.zshrc`) to add an export line. This should go somewhere after the `eval "$(pyenv init --path)"`:
```bash
 export PIPENV_VENV_IN_PROJECT=1
 ```

## Configuring Git and GitHub

### Update Git
1. Type ```sudo add-apt-repository ppa:git-core/ppa``` and press ``<Enter>`` to add a package repository for downloading the latest version of Git. Follow the prompts in the terminal.
2. Type ``sudo apt update ``and press ``<Enter>`` to update your local repository cache.
3. Type ``sudo apt install git`` and press ``<Enter>`` to install the latest version of Git
4. Type ``git --version``

### Configure Git
1. Type ``git config --global color.ui true`` and press ``<Enter>``
2. Type ``git config --global user.name`` + ``<Space>`` + your name and press <Enter> (Note: this should be your full name, not your GitHub username, in quotes.)
3. Type ``git config --global user.email`` + ``<Space>`` + the email address you used to sign up to GitHub and press `<Enter>`
4. Type `git config --global init.defaultBranch main` to update the default branch nameLinks to an external site. to main
5. Type `ssh-keygen` and press `<Enter>`. For each prompt **do not type anything**, just continue to press `<Enter>`. It's particularly important that you **do not enter a passphase;** you should leave the passphrase empty when prompted. If you enter a passphrase here, you'll have to enter it every time you interact with GitHub (which will happen a lot during the program). You may also run into issues submitting assignments later.
6. Type `cat ~/.ssh/id_rsa.pub | clip.exe` and press `<Enter>`. This will copy your SSH key to your clipboard
7. Open the [GitHub New SSH key form](https://github.com/settings/ssh/newLinks) (*Note: you need to be logged in to GitHub to access that link.*)
8. Type "My personal PC" in the "Title" input field
9. Paste what's on your clipboard from step seven in the "Key" input field
10. Click "Add SSH Key"

## Configuring Bitbucket
1. Generate an SSH key pair by typing:
```bash
 ssh-keygen -t ed25519 -C "your.email@example.com"
```
*Replace with your Bitbucket email address*
- When prompted for the file location, just press Enter to use the default location
- You'll then be asked to enter a passphrase. You can either:
    - Press Enter twice for no passphrase (less secure but more convenient)
    - Or enter a passphrase you'll remember (more secure)
    **I'd advice against putting any passphrase as sometimes you may forgrt it**
2. Start the SSH agent
```bash
eval "$(ssh-agent -s)"
```
3. Add your SSH private key to the agent:
```bash
ssh-add ~/.ssh/id_ed25519
```
4. Copy your public key:
```bash
cat ~/.ssh/id_ed25519.pub
```
5. Add the key to Bitbucket:
- Log into Bitbucket
- Go to your profile settings (click your profile picture → Settings)
- In the left sidebar, click "SSH keys"
- Click "Add key"
- Paste your public key and give it a title (like "WSL Ubuntu")
6. Test your SSH connection:
```bash
ssh -T git@bitbucket.org
```


