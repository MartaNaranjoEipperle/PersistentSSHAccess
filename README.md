## PersistentSSHAccess

This repository provides a solution for persistently storing and easily accessing SSH connections. Avoid repeatedly typing long SSH commands by managing configurations for recurring access to different hosts. Ideal for automating and simplifying SSH connections across various environments and scenarios.

### Troubleshooting Steps:

#### Installing Zsh Completions:

Ensure the Zsh Completions plugin is installed. If using Homebrew, you can install it with the following command:
```sh
brew install zsh-completions
```

#### Open your ~/.zshrc file with a text editor (e.g., nano, vim):
```sh
nano ~/.zshrc
```

#### Add the following alias to define the SSH command with customized values for ```<hostname>``` and ```<ip-address>```:
```sh
# Alias for SSH access to a specific host
alias sshhost1='ssh -o StrictHostKeyChecking=False -i ~/.ssh/da/demo_ed25519 <hostname>@<ip-address>'
```

Replace ```<hostname>``` with the actual hostname of your server and ```<ip-address>``` with the actual IP address.

#### Adding Zsh Completions to Zsh Configuration:

Add the following lines to your ~/.zshrc file to enable Zsh Completions:
```sh
if type brew &>/dev/null; then
    FPATH=$(brew --prefix)/share/zsh-completions:$FPATH

    autoload -Uz compinit
    compinit
fi
```

#### Ensure Angular CLI completion script is loaded correctly:

The issue might be related to the Angular CLI completion script. Try including the completion script in your ~/.zshrc file after initializing compinit:
```sh
# Zsh Completions
if type brew &>/dev/null; then
    FPATH=$(brew --prefix)/share/zsh-completions:$FPATH

    autoload -Uz compinit
    compinit
fi

# Load Angular CLI autocompletion
if [ -f <(ng completion script) ]; then
    source <(ng completion script)
fi
```

Save the file (Ctrl + O in nano, followed by Enter) and exit the editor (Ctrl + X in nano).

#### After making changes, reload your ~/.zshrc file to apply the updates:
```sh
source ~/.zshrc
```
