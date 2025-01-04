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

## **Configure VS Code to Work with WSL**
1. Open the "Visual Studio Code" application using the "Start" menu
2. Click **"View"** in the toolbar, then click **"Extensions"** in the dropdown menu, or use the shortcut `<Control>` + `<Shift>` + `X`.
3. Search for **"WSL"** and click on the item in the list with a description that starts with "Open any folder in the Windows Subsystem for Linux (WSL) …".
4. Click the **"Install"** button near the top of the page
5. Click **"Terminal"** in the toolbar, then click **"New Terminal"** (Note: a new terminal should appear at the bottom of your VS Code window)
6. If the dropdown in your terminal says **"1: wsl"**, continue to step 9. Otherwise, click on the dropdown in the terminal that says **"1: powershell"** and choose **"Select Default Profile"**
7. A dropdown should appear at the top of your VS Code window
8. Click on **"Ubuntu (WSL)"** to enable VS Code to display your Ubuntu terminal
9. Close the **"Visual Studio Code"** application
10. Open the **"Ubuntu"** application using the "Start" menu
11. Type ``code`` and press `<Enter>`

*If the **"Visual Studio Code"** application opens when you type code in the "Ubuntu" application, your vscode has been configured successfully*

## Installing MYSQL and PHPMYAdmin on WSL

1. Update your system by
```bash
sudo apt update
```
2. Then upgrade 
```bash
sudo apt upgrade -y
```
3. Install MYSQL Server
```bash
sudo apt install mysql-server
```
4. Check the list of running services to ensure mysql is running
```bash
service --status-all
```
5. Run the MYSQL secure installation script. 
```bash
sudo mysql_secure_installation
```
 - When asked if you want to impose password security you can type **yes** or **NO** depending. *If you know you will forget the password i'd recommend not seeting one*
 - For password difficult select 2
 - The remaining questions you should select **yes** for all of them
6. Type `sudo mysql` to access the myql
7. Use the following command to set a MYSQL password for the root user and also change its authentication method to MYSQL Native password
```sql
alter user ‘root’@‘localhost’ identified with mysql_native_password by ‘Password1’;
```
8. To login to mysql type the following command input your password
```bash
msql -u root -p
```
9. Install phpMyadmin
```bash
sudo apt install phpmyadmin
```
10. When you get the dialogue to choose the web server, choose **Apache 2**
11. When asked to use Auto configuration choose **No**
12. Install php
```bash
sudo apt install php
```
13. Login to the database using phpmyadmin by typing the following command and copying the ip address
```bash
ip a
```
14. Go to your browser and paste the ip copied above. Add **/phpmyadmin** infront of the the ip 
eg
