# General

## Can my data be recovered once I've terminated my instance?

{% hint style="danger" %}
We cannot recover your data once you've terminated your instance! Before terminating an instance, make sure to back up all data that you want to keep.

If you want to save data even after you terminate your instance, create a [persistent storage file system](https://lambdalabs.com/blog/persistent-storage-beta/).
{% endhint %}

{% hint style="info" %}
The persistent storage file system must be attached to your instance _before_ you start your instance. The file system cannot be attached to your instance after you start your instance.

When you create a file system, a directory with the name of your file system is created in your home directory. For example, if the name of your file system is **PERSISTENT-FILE-SYSTEM**, the directory is created at `/home/ubuntu/PERSISTENT-FILE-SYSTEM`. **Data not stored in this directory is erased once you terminate your instance and cannot be recovered.**
{% endhint %}

## Can I pause my instance instead of terminating it?

It currently isn't possible to pause (suspend) your instance rather than terminating it. But, this feature is in the works.

Until this feature is implemented, you can use persistent storage file systems to imitate some of the benefits of being able to pause your instance.

## Do you support Kubernetes (K8s)?

We currently don't support Kubernetes, also known as K8s.
