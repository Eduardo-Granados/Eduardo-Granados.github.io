<font color="#ff0000"> # [STILL UPDATING] </font>


# Connecting account with SSH and cloning a directory

<br>

### Github

[Link 1](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

[Link 2](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#switching-remote-urls-from-https-to-ssh)

<br>

### Git

[Git Help](https://git-scm.com/book/en/v2/GitHub-Account-Setup-and-Configuration)

<br>

### Stackoverflow Help

[Link 1](https://stackoverflow.com/questions/8840551/configuring-user-and-password-with-git-bash)

```text
Make sure you are using the SSH URL for the GitHub repository rather than the HTTPS URL. It will ask for username and password when you are using HTTPS and not SSH. You can check the file .git/config or run git config -e or git remote show origin to verify the URL and change it if needed.

You can change the URL with: [1]

git remote set-url origin git+ssh://git@github.com/username/reponame.git
```

[Link 2](https://stackoverflow.com/questions/6565357/git-push-requires-username-and-password)

```
A common cause is cloning using the default (HTTPS) instead of SSH. You can correct this by going to your repository, clicking "Clone or download", then clicking the "Use SSH" button above the URL field and updating the URL of your origin remote like this:

git remote set-url origin git@github.com:username/repo.git

You can check if you have added the remote as HTTPS or SSH using:

git remote -v
```

