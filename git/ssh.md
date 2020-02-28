[GitHub - List of your SSH Keys](https://github.com/settings/keys)

How to setup SSH on your machine and connect it to the Server
Short Sumamry how to manage ssh keys for multiple accounts [Gist](https://gist.github.com/jexchan/2351996)
additional commands:
- ```ssh-add -D ``` delete all cached keys
- ```ssh-add -l ``` check saved keys
- [Instructions from GitHub on how to set up ssh](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
additional: ⭐[setting ssh and git on Windows 10](https://dev.to/bdbch/setting-up-ssh-and-git-on-windows-10-2khk)
  - good article
  - To use Source Tree with SSH you need this [article](https://community.atlassian.com/t5/Sourcetree-questions/SSH-not-working-on-SourceTree/qaq-p/208971)



~/.ssh dir
- here you store your ssh keys
- there is always 2 of them with the same name (private and public one (has the extension ".pub"))
  - public one is sent to the Server (e.g., GitHub, GitLab)
- *config* file should enable you to work even without starting ssh-agent like that
  - use it to set up a per user configuration file where you can store different SSH options for each remote machine you connect to
  - specifies which file should be matched when the domain of origin maps to some destination in config file

* In Windows, while using WSL sometimes I had issue to clone projects using WSL shell but it did work in git-bash
  - because Windows and WSL do not share the same rights for .ssh folder or something like that
  - **Solution**:
    - [How to share keys between Windows and wsl-2](https://devblogs.microsoft.com/commandline/sharing-ssh-keys-between-windows-and-wsl-2/)

TL;DR/Instructions
- In Windows 2 prerequisites:
  - use git-bash
  - Enable local ssh-agent service in Windows [article](https://www.richardkotze.com/top-tips/connecting-github-with-openssh-windows)
    - search for "troubleshooting part"
    - ssh-agent service should be set from **disabled** to **automatically started**
1. create ssh-key
  - ```ssh-add …```
    - in windows (git-bash): ```eval $(ssh-agent)```
3. set config file in /.ssh directory
    - [SO Link about config file](https://stackoverflow.com/questions/3225862/multiple-github-accounts-ssh-config)
4. add public key to github
   - [GitHub - List of your SSH Keys](https://github.com/settings/keys)
- This should be enough to use git with multiple GitHub and GitLab accounts
