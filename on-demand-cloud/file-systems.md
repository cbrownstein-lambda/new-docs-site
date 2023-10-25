# File systems

## What are file systems (persistent storage)?

File systems, also known as persistent storage, allow you to store your large datasets and the state of your instance, for example:

* Packages installed system-wide using `apt-get`.
* Python packages installed using `pip`.
* [conda](../software/virtual-environments-and-docker-containers.md#creating-a-conda-virtual-environment) and [Python venv](../software/virtual-environments-and-docker-containers.md#creating-a-python-virtual-environment) virtual environments.

Lambda GPU Cloud file systems have a capacity of 8 exabytes, or 8,000,000 terabytes, and you can have a total of 24 file systems, except for file systems created in the Texas, USA (us-south-1) region. The capacity of file systems created in the Texas, USA (us-south-1) region is 10 terabytes.

## Can file systems be accessed without an instance?

Persistent storage file systems can't be accessed unless attached to an instance _at the time the instance is launched_.

For this reason, _it's recommended that you keep a local copy of the files you have saved in your persistent storage file systems_. This can be done using `rsync`.

{% hint style="info" %}
File systems can't be attached to running instances and can't be mounted remotely, for example, using NFS.

Moreover, file systems can only be attached to instances in the same region. For example, a file system created in the us-west-1 (California, USA) region can only be attached to instances in the us-west-1 region.

File systems can't be transferred from one region to another. However, you can copy data between file systems using tools such as `rsync`.

Lambda GPU Cloud currently doesn't offer block or object storage.
{% endhint %}

## Can I set a limit (quota) on my file system usage?

Currently, you can't set a limit (quota) on your persistent storage file system usage.

You can see the usage of a persistent storage file system from within an instance by running `df -h -BG`. This command will produce output similar to:

```
Filesystem           1G-blocks  Used   Available Use% Mounted on
udev                       99G    0G         99G   0% /dev
tmpfs                      20G    1G         20G   1% /run
/dev/vda1                1357G   23G       1335G   2% /
tmpfs                      99G    0G         99G   0% /dev/shm
tmpfs                       1G    0G          1G   0% /run/lock
tmpfs                      99G    0G         99G   0% /sys/fs/cgroup
persistent-storage 8589934592G    0G 8589934592G   0% /home/ubuntu/persistent-storage
/dev/vda15                  1G    1G          1G   6% /boot/efi
/dev/loop0                  1G    1G          0G 100% /snap/core20/1822
/dev/loop1                  1G    1G          0G 100% /snap/lxd/24061
/dev/loop2                  1G    1G          0G 100% /snap/snapd/18357
tmpfs                      20G    0G         20G   0% /run/user/1000
```

In the example output, above:

* The name of the file system is `persistent-storage`.
* The size of the file system is `8589934592G` (8 exabytes).
* The available capacity of the file system is `8589934592G`.
* The used percentage of the file system is `0%`.
* The file system is mounted on `/home/ubuntu/persistent-storage`.

{% hint style="success" %}
You can also use the Cloud API's `/file-systems` endpoint to find out your file system usage.
{% endhint %}
