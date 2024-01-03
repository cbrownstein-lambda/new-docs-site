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
