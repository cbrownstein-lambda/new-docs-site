# Basic Linux commands and system administration

## Importing SSH keys from GitHub accounts

To import an SSH key from a GitHub account and add it to your server (or Lambda GPU Cloud on-demand instance):

1.  Using your existing SSH key, SSH into your server.

    Alternatively, if you're using an on-demand instance, open a terminal in [Jupyter Notebook](https://docs.lambdalabs.com/cloud/open-jupyter-notebook/).
2.  Import the SSH key from the GitHub account by running:

    ```bash
    ssh-import-id gh:USERNAME
    ```

    Replace **USERNAME** with the GitHub account’s username.

If the SSH key is successfully imported, `ssh-import-id` will output a message similar to:

```
2023-08-04 15:03:52,622 INFO Authorized key ['256', 'SHA256:C6pl0q4evVYZWcyByVF69D6fdbdKa7F8ei8V2F/bTW0', 'cbrownstein-lambda@github/67649580', '(ED25519)']
2023-08-04 15:03:52,623 INFO [1] SSH keys [Authorized]
```

If the SSH key _isn't_ successfully imported, `ssh-import-id` will output a message similar to:

```
2023-08-04 15:06:36,425 ERROR Username "fake-cbrownstein-lambda" not found at GitHub API. status_code=404 user=fake-cbrownstein-lambda
```

## Using rsync to copy and synchronize files

`rsync` is a tool that you can use to copy files between your computer and a remote server.

`rsync` can also be used to copy files directly between remote servers, bypassing your computer entirely.

{% hint style="success" %}
`rsync` is useful for copying files between Cloud persistent storage file systems in different regions.
{% endhint %}

{% hint style="info" %}
`rsync` copies files using SSH. For this reason, to copy files between your computer and a remote server, you need to be able to SSH into the remote server.

To use `rsync` to copy files between remote servers directly, you need to be able to SSH into the remote servers using public key authentication with an SSH agent.
{% endhint %}

### Copy files between your computer and a remote server

To copy files from your computer to a remote server using`rsync`, run:

```bash
rsync -av --info=progress2 FILES USERNAME@SERVER-IP:REMOTE-PATH
```

Replace **FILES** with the files you want to copy to the remote server. Alternatively, you can specify a directory.

Replace **USERNAME** with your username on the remote server.

Replace **SERVER-IP** with the IP address of the remote server.

Replace **REMOTE-PATH** with the directory into which you want to copy files.

In the below example, `rsync` was used to copy the local directory `rsync_example_dir`, containing a single empty file named `EXAMPLE_FILE`, into the home directory of the user `ubuntu` on a remote server with the IP address `146.235.208.193`.

```
$ rsync -a --progress rsync_example_dir ubuntu@146.235.208.193:~
sending incremental file list
rsync_example_dir/
rsync_example_dir/EXAMPLE_FILE
              0 100%    0.00kB/s    0:00:00 (xfr#1, to-chk=0/2)
```

### Copy files directly between remote servers

{% hint style="info" %}
To copy files directly between remote servers using `rsync`, you must use public key (rather than password) authentication for SSH with an SSH agent.

You can add your private key to the SSH agent by running:

```bash
ssh-add SSH-PRIVATE-KEY
```

Replace **SSH-PRIVATE-KEY** with the path to your SSH private key, for example, `~/.ssh/id_ed25519`.

You can confirm your key was added to the SSH agent by running:

```bash
ssh-add -L
```

Your public key will be listed in the output.
{% endhint %}

To copy files directly between remote servers using `rsync`, first SSH into the server you want to copy files _from_ by running:

```bash
ssh -A USERNAME-1@SERVER-IP-1
```

Replace **SERVER-IP-1** with the IP address of the server you want to copy files from, referred to below as _Server 1_.

Replace **USERNAME-1** with your username on _Server 1_.

{% hint style="success" %}
It's recommended to run the `rsync` command, below, in a `tmux` or `screen` session. This way, you can log out of _Server 1_ and the `rsync` command will continue to run.
{% endhint %}

Then, on _Server 1_, run:

```bash
rsync -av --info=progress2 FILES USERNAME-2@SERVER-IP-2:REMOTE-PATH
```

Replace **SERVER-IP-2** with the IP address of the server you want to copy files _to_, referred to below as _Server 2_.

Replace **FILES** with the files (or directory) you want to copy to _Server 2_.

Replace **USERNAME-2** with your username on _Server 2_.

Replace **SERVER-IP-2** with the IP address of _Server 2_.

Replace **REMOTE-PATH** with the directory into which you want to copy files.

## Preventing system from suspending or sleeping

To prevent your system from going to sleep or suspending, run:

```sh
sudo systemctl mask hibernate.target hybrid-sleep.target \
suspend-then-hibernate.target sleep.target suspend.target
```

### Creating additional user accounts in Ubuntu Desktop

By having their own accounts, users can manage their own files, datasets, and programs, as well as manage their own [Python virtual environments](https://docs.lambdalabs.com/linux/create-python-virtual-environment/), [conda virtual environments](https://docs.lambdalabs.com/linux/create-conda-virtual-environment/), and [Docker containers](https://docs.lambdalabs.com/linux/install-docker-run-container/).

Also, by having additional accounts, you can assign system administrator privileges to other users.

You can add user accounts from the **Users** panel in **GNOME Settings**:

1. Press the Super key on your keyboard to open the **Activities** overview. Then, type `users`.

{% hint style="success" %}
The Super key on your keyboard is located between the **Ctrl** and **Alt** keys.

![](https://docs.lambdalabs.com/lib/images/super-key.svg)
{% endhint %}

1. Click **Users** to open the **Users** panel in **GNOME Settings**.
2. Click **Unlock** at the top of the panel, then click **Add User**.
3. For **Account Type**, choose either **Standard** or **Administrator**.
   * **Standard** account users can create, modify, and delete only their own files, not system files or other users' files. Standard account users also can change their own settings only, not system settings or other users’ settings.
   * **Administrator** account users have the same privileges as standard account users. However, administrator account users can also create, modify, and delete system files and other users' files. Administrator account users can also change their system settings and other users' settings.
4. For **Full Name**, enter the user's full name, that is, their "real" name or name they use to identify themselves.
5. For **Username**, enter the name the user will use to log into the system. This name will also be the name of the user's home directory, for example, `/home/username`.
6.  Under **Password**, choose either **Allow user to set a password when they next login**, or **Set a password now**.\


    If you choose to set a password now, in the **Password** field, enter a custom password, or click the ![](https://docs.lambdalabs.com/lib/images/settings-symbolic.svg) to automatically generate a password.
7. Click **Add** at the top of the dialog to add the user.
