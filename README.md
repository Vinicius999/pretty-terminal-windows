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


### 7 - Nerd Font installation

Open Windows Terminal **as administrator** to start installing the font from the [NERD FONTS repository](https://ohmyposh.dev/docs/installation/fonts) and execute the command:

```
oh-my-posh font install
```

Select the font Hack like is shown in the image below:

![nerd-font-install](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/nerd-font-install.png)

To test the installation, open a new PowerShell (without admin) and go to Settings -> Windows PowerShell -> Appearance like is shown in the image below:

![nerd-font-install](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/powershell-font.gif)

Select `Hack Nerd Font` Save and close the terminal.


### 8 - Creating a PowerShell profile

Open a new terminal as administrator and run the command below to confirm which Shell is in use.

```
oh-my-posh get shell
```

Try editing your PowerShell profile script using the first command below. If you get an error, run the second command.

```
notepad $PROFILE
```

```
New-Item -Path $PROFILE -Type File -Force
```

The file will be created in the following path `C:\Users\<USER-NAME>\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1`.

### 9 - Allowing local scripst

Allow the execution of local scripsts and request that only remote scripsts be signed:

```
Set-ExecutionPolicy RemoteSigned
```

Open the file `C:\Users\<USER-NAME>\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1` using the command:

```
notepad $PROFILE
```

Add the following line to the file and save:

```
oh-my-posh init pwsh | Invoke-Expression
```

Open a new PowerShel (without admin) reload your profile for the changes to take effect.

```
. $PROFILE
```

### 10 - Setting up Oh My Posh theme in PowerShell

To configure a theme, run the command below to list all available themes.

```
Get-PoshThemes
```

All themes can also be viewed on the [themes page](https://ohmyposh.dev/docs/themes) of the Oh My Posh documentation: [`https://ohmyposh.dev/docs/themes`](https://ohmyposh.dev/docs/themes).

Open the profile configuration file again (`C:\Users\<USER-NAME>\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1`) and paste the example command changing to your chosen theme. No exemplo abaixo, o tema escolhido foi o [blue-owl](https://ohmyposh.dev/docs/themes#blue-owl):

```
oh-my-posh init pwsh --config 'C:\Users\<USER_NAME>\AppData\Local\Programs\oh-my-posh\themes\blue-owl.omp.json' | Invoke-Expression
```

To test a new theme, copy the name of the theme as shown below and replace it in the command below.

![blue-owl-theme](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/blue-owl-theme.png)

```
oh-my-posh init pwsh --config 'C:\Users\<USER_NAME>\AppData\Local\Programs\oh-my-posh\themes\<THEME-NAME>.omp.json' | Invoke-Expression
```

### 11 - Setting up Oh My Posh theme in Git Bash

Search for the .zshrc file in Windows Explorer. It's usually in the path C:\Users\<USER-NAME>

Open the file with VS Code and add the following commands to the end of the file:

```
if [ "$TERM_PROGRAM" != "Apple_Terminal" ]; then
  eval "$(oh-my-posh init zsh --config C:/Users/<USER-NAME>/AppData/Local/Programs/oh-my-posh/themes/blue-owl.omp.json)"
fi
```

Note que o cominho especificado após a flag `--config` é o mesmo caminho especificado no comando para configurar um tema no PowerShell.


### 11 - Setting up Nerd FOnts in Visual Studio Code

When using Visual Studio Code, you will need to configure the integrated Terminal to make use of the Nerd Font as well. This can be done by changing the `Integrated: Font Family` value in the Terminal settings, default shortcut: `CTRL + ,` and search for `Integrated: Font Family` or via `File` -> `Preferences` -> `Settings` and search for `Integrated: Font Family` like is shown in the image below:

![vs-code-nerd-fonts](https://github.com/Vinicius999/pretty-terminal-windows/blob/main/images/vs-code-nerd-fontst.gif)

Close VS Code e open again. The icons must be enabled in the terminal

### 12 - References and documentatio
Explore options and other topics in the documentation.
- ZSH official site: https://www.zsh.org/
- Oh My Posh Documentation: https://ohmyposh.dev/docs
