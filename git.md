# Git
### git-setup
> [Download & Install Git](https://git-scm.com/download)
```
# Set git configuration
git config --global user.name "MyUserName>"
git config --global user.email "MyEmail@Addr.ess"

# Remove any existing ssh-keys
cd ~/.ssh
rm id_rsa*

# Setup SSH key for communicating with GitServer
ssh-keygen -t rsa -C "MyEmail@Addr.ess"
# Input a *KEY* for SSH key generation
# Copy contents of ~/.ssh/id_rsa.pub & paste in github/bitbucket->settings->ssh-key

# Verify setup
ssh -T git@gitServer
# e.g. ssh -T git@github.com
```

### Git revert uncommitted changes
```
git reset
git checkout .
git clean -fdx
```
