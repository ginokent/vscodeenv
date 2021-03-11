# vscodeenv

Install fixed version Visual Studio Code and fixed version extensions in idempotent.  

**As of 2021-03-10, only Darwin is supported.**  

# Installing

```bash
wget https://github.com/djeeno/vscodeenv/releases/latest/download/vscodeenv-darwin-amd64 --output-document=/usr/local/bin/vscodeenv && chmod -v +x /usr/local/bin/vscodeenv
```

# Usage

```console
$ vscodeenv

vscodeenv is a tool for helping to install specific version 'Visual Studio Code'

Usage:

  vscodeenv <command> [arguments]

The commands are:

    freeze      Generate version lock script

    install     Install specific version 'Visual Studio Code'

                arguments
                    <version>
                        'Visual Studio Code' version
                        If not given, install latest version
                options
                    -f, --fource
                        Fource install

    kill        Kill '/Applications/Visual Studio Code.app'

    list        List installable 'Visual Studio Code' versions

                arguments
                    -1, --one-column
                        If you want to output a single column, add this option

    self-update Update 'vscodeenv' itself

```

If you want to generate version lock script, run `vscodeenv freeze`.  
( `vscodeenv freeze` is inspired by [`pip freeze`](https://pip.pypa.io/en/stable/reference/pip_freeze/) )  

output example:  

```
$ vscodeenv freeze
#!/bin/sh
# Code generated by vscodeenv freeze; This code is vscodeenv version lock script.
set -eu

# Visual Studio Code
vscodeenv install 1.54.1

# Extensions
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension Unity.unity-debug@3.0.2 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension VisualStudioExptTeam.vscodeintellicode@1.2.11 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension bierner.markdown-mermaid@1.9.2 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension eamodio.gitlens@11.3.0 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension golang.go@0.23.0 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension mads-hartmann.bash-ide-vscode@1.11.0 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension ms-dotnettools.csharp@1.23.9 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension ms-vscode-remote.remote-containers@0.163.2 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension ms-vscode-remote.remote-ssh-edit@0.65.1 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension ms-vscode-remote.remote-ssh@0.65.1 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension ms-vsliveshare.vsliveshare@1.0.3912 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension timonwong.shellcheck@0.13.2 --force
'/Applications/Visual Studio Code.app/Contents/Resources/app/bin/code' --install-extension zxh404.vscode-proto3@0.5.3 --force
```

Generate a version lock script and then install from it in another environment.

```console
1. Generate a version lock script
$ vscodeenv freeze > vscodeenv.lock.sh

2. Run vscodeenv.lock.sh as shell script (require vscodeenv)
$ sh vscodeenv.lock.sh
```
