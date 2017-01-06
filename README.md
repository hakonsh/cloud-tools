# cloud-tools

The terragrunt-wrapper requires a [passwordstore](https://www.passwordstore.org).

## Required software

```
brew install terraform go pass
```

Download Terragrunt from https://github.com/gruntwork-io/terragrunt/releases

_(select the released file `terragrunt_darwin_amd64` from the newest release that has this package)_

```
cd ~/Downloads
chmod 0755 ~/Downloads/terragrunt_darwin_amd64
mv ~/Downloads/terragrunt_darwin_amd64 /usr/local/bin/
ln -nsf /usr/local/bin/terragrunt_darwin_amd64 /usr/local/bin/terragrunt

```

## Insert into .bashrc

`path-to-your-sourcecode/go` should be an empty folder you create to store your go code in.

```
export GOPATH=<path-to-your-sourcecode>/go
export GOBIN=$GOPATH/bin
PATH=$GOBIN:$PATH
export PATH
```

## Set up developer environment

```
source ~/.bashrc
mkdir -p $GOPATH/{bin,pkg,src/github.com/nsbno,vendor}
go get github.com/nsbno/cloud-tools # Ignore the warning message
cd $GOPATH/src/github.com/nsbno/cloud-tools
./deps.sh
./make.sh
```

## Install envchain to set aws credentials
```
brew install envchain
envchain --set aws AWS_ACCESS_KEY_ID AWS_SECRET_ACCESS_KEY
```
See: https://github.com/sorah/envchain

## Test it!

Run `envchain aws terragrunt-wrapper plan` in a terraform base directory to check if it works.

---
The tools has borrowed a lot from: https://github.com/digipost/cloud-tools
