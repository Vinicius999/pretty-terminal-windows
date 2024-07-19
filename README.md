<h1 align="center">Pretty Terminal in Windows</h1>

## Main programs 

<p style='margin: 20px 4px 32px;'>
    <a href="https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH" target="_blank" rel="noopener noreferrer">
        <img src="https://github.com/Zsh-art/logo/blob/main/png/white_horizontal_icon.png?raw=true" alt="Vini-zsh" width="88" height="58" />
    </a>_
    <a href="https://ohmyposh.dev/" target="_blank" rel="noreferrer">
        <img src="https://raw.githubusercontent.com/jandedobbeleer/oh-my-posh/main/website/static/img/logo.png" alt="Vini-oh-my-posh" width="90" height="60" />
    </a>
</p>

## Step-by-step

### 1 - Download ZSH 

Download the latest zsh package from the link: [download-zsh](https://packages.msys2.org/package/zsh?repo=msys&variant=x86_64)

The correct file to download is shown in the image below:

![zsh-download](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/link-download-zsh.png)

The name of the downloaded file should look like `zsh-5.9-2-x86_64.pkg.tar.zst`.


### 2 - Download and install PeaZip

Download PeaZip from the link: [download-peazip](https://peazip.github.io/index.html)

PeaZip is used to extract the `.ZST` files, like the ZSH packege downloaded before.


### 3 - Extract the ZSH file to your git bash installation dir

Move the `zsh-5.9-2-x86_64.pkg.tar.zst` file to git bash installation dir, usually the path is `C:\Program Files\Git`, like is shown in the image below:

![git-installation-dir](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/git-installation-dir.png)

Extract the file using PeaZip like is shown in the image below:

![extract-zsh-peazip](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/extract-zsh-peazip.png)

Will be extracted a file that looks like `zsh-5.9-2-x86_64.pkg.tar` with `.TAZ` extention. You should extract it in the same way as the initial file.

### 4 - Testing ZSH

Open Git Bash and execute the command:
```
zsh
```

### 5 - Setting zsh as the default

To make sure that **zsh** will run every time you open Git Bash, look in Windows Explorer for the `.bashrc` file and open it with **VS Code** like is shown in the image below:

![extract-zsh-peazip](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/bashrc-file.png)

Add the following lines at the end of the file:

```
# Launch Zsh
if [ -t 1 ]; then
    exec zsh
fi
```

Save, close and open again the Git Bash. The ZSH should be executed automatically.

### 6 - Oh My Posh installation

Open PowerShell and run the command:

```
winget install JanDeDobbeleer.OhMyPosh -s winget
```

After running the command and getting a successful installation, close the terminal.


### 6 - Nerd Font installation

Open Windows Terminal **as administrator** to start installing the font from the [NERD FONTS repository](https://ohmyposh.dev/docs/installation/fonts) and execute the command:

```
oh-my-posh font install
```

Select the font Hack like is shown in the image below:

![nerd-font-install](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/nerd-font-install.png)

To test the installation, open a new PowerShell (without admin) and go to Settings -> Windows PowerShell -> Appearance like is shown in the image below:

![nerd-font-install](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/powershell-font.gif)