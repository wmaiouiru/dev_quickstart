# Mac


## Install brew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Init brew
```
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```


## Add ssh key
Add ssh key
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account?tool=webui

```
ssh-keygen -t ed25519 -C "<email_address>"
eval "$(ssh-agent -s)"
pbcopy < ~/.ssh/id_ed25519.pub
```



## Setting up Python Environment


Reference: https://realpython.com/intro-to-pyenv/


```
brew install openssl readline sqlite3 xz zlib
curl https://pyenv.run | bash
```

### Install python version and set as global
```
pyenv install 3.11
pyenv global 3.11
```

## Install n and npm
```
brew install node
```

## Install Bazel
```
brew install bazel
```

## Change git to use nano
```
git config --global core.editor "nano"
```