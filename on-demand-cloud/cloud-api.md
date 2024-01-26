# Cloud API

With the [Cloud API](https://cloud.lambdalabs.com/api/v1/docs), you can:

* [Launch instances](cloud-api.md#launching-instances), [restart instances](cloud-api.md#restarting-instances), and [terminate instances](cloud-api.md#terminating-instances).
* [List the details of all of your instances](cloud-api.md#listing-details-of-running-instances).
* [Get the details of a running instance](cloud-api.md#getting-details-of-a-specific-instance).
* [Get a list of the instance types offered by Lambda GPU Cloud](cloud-api.md#listing-instances-types-offered-by-lambda-gpu-cloud).
* [Manage your SSH keys](cloud-api.md#managing-ssh-keys).
* [List your file systems](cloud-api.md#listing-file-systems).

{% hint style="info" %}
Requests to the Cloud API are generally limited to 1 request per second.

Requests to the `/instance-operations/launch` endpoint are limited to 1 request every 10 seconds.
{% endhint %}

## Launching instances

You can launch an instance from the command line using the [Cloud API](https://cloud.lambdalabs.com/api/v1/docs):

1. [Generate an API key](https://cloud.lambdalabs.com/api-keys).
2.  Create a file named `request.json` that contains the [necessary payload](https://cloud.lambdalabs.com/api/v1/docs#operation/launchInstance). For example:

    ```json
    {
      "region_name": "us-east-1",
      "instance_type_name": "gpu_1x_a100_sxm4",
      "ssh_key_names": [
        "SSH-KEY"
      ],
      "file_system_names": [],
      "quantity": 1
    }
    ```
3.  Run the following command:

    ```bash
    curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/instance-operations/launch -d @request.json -H "Content-Type: application/json" | jq .
    ```

Replace **API-KEY** with your actual API key. **Don't remove the trailing colon (:).**

## Restarting instances

1. [Generate an API key](https://cloud.lambdalabs.com/api-keys) if you haven't already generated one.
2.  Create a file that contains the [necessary payload](https://cloud.lambdalabs.com/api/v1/docs#operation/restartInstance). For example:

    ```json
    {
      "instance_ids": [
        "0920582c7ff041399e34823a0be62549"
      ]
    }
    ```

{% hint style="info" %}
[Use the API to obtain the IDs of your instances](https://docs.lambdalabs.com/cloud/list-running-instances/).
{% endhint %}

3. Run the following command:

```bash
curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/instance-operations/restart -d @INSTANCE-IDS -H "Content-Type: application/json" | jq .
```

Replace **API-KEY** with your actual API key. **Don't remove the trailing colon (:).**

Replace **INSTANCE-IDS** with the name of the payload file you created in the previous step.

## Terminating instances

1. [Generate an API key](https://cloud.lambdalabs.com/api-keys) if you haven't already generated one.
2.  Create a file that contains the [necessary payload](https://cloud.lambdalabs.com/api/v1/docs#operation/terminateInstance). For example:

    ```json
    {
      "instance_ids": [
        "0920582c7ff041399e34823a0be62549"
      ]
    }
    ```

    **Note**

{% hint style="info" %}
[Use the API to obtain the IDs of your instances](cloud-api.md#listing-details-of-running-instances).
{% endhint %}

3. Run the following command:

```bash
curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/instance-operations/terminate -d @INSTANCE-IDS -H "Content-Type: application/json" | jq .
```

Replace **API-KEY** with your actual API key. **Don't remove the trailing colon (:).**

Replace **INSTANCE-IDS** with the name of the payload file you created in the previous step.

## Listing details of running instances

You can list your running instances from a command line using the [Cloud API](https://cloud.lambdalabs.com/api/v1/docs).

First, [generate an API key](https://cloud.lambdalabs.com/api-keys). Then, run the following command:

```bash
curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/instances | jq .
```

Replace **API-KEY** with your actual API key. **Don't remove the trailing colon (:).**

## Getting details of a specific instance

You can retrieve the details of an instance from a command line using the [Cloud API](https://cloud.lambdalabs.com/api/v1/docs).

First, [generate an API key](https://cloud.lambdalabs.com/api-keys). Then, run the following command:

```bash
curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/instances/INSTANCE-ID | jq .
```

Replace **API-KEY** with your actual API key. **Don't remove the trailing colon (:).**

Replace **INSTANCE-ID** with the ID of the instance you want details about.

## Listing instances types offered by Lambda GPU Cloud

You can list the instances types offered by Lambda GPU Cloud by first [generating an API key](https://cloud.lambdalabs.com/api-keys), then running the following command:

```bash
curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/instance-types | jq .
```

Replace **API-KEY** with your actual API key. **Don’t remove the trailing colon (:).**

## Managing SSH keys

You can use the [Cloud API](https://cloud.lambdalabs.com/api/v1/docs) to:

* [Add an existing SSH key to your account](https://docs.lambdalabs.com/cloud/api-add-ssh-key/#add-an-existing-ssh-key-to-your-account).
* [Generate a new SSH key pair](https://docs.lambdalabs.com/cloud/api-add-ssh-key/#generate-a-new-ssh-key-pair).
* [List the SSH keys saved in your account](https://docs.lambdalabs.com/cloud/api-add-ssh-key/#list-the-ssh-keys-saved-in-your-account).
* [Delete an SSH key from your account](https://docs.lambdalabs.com/cloud/api-add-ssh-key/#delete-an-ssh-key-from-your-account).

**Note**

{% hint style="info" %}
Following these instructions won't add the SSH key to existing instances.

To add SSH keys to existing instances, read our FAQ on [using more than one SSH key](https://docs.lambdalabs.com/cloud/more-than-one-ssh-key/).
{% endhint %}

{% hint style="info" %}
You can add up to 1,024 SSH keys to your account.
{% endhint %}

### Add an existing SSH key to your account <a href="#add-an-existing-ssh-key-to-your-account" id="add-an-existing-ssh-key-to-your-account"></a>

To add an existing SSH key to your account:

1. [Generate an API key](https://cloud.lambdalabs.com/api-keys) if you don't have one already.
2.  Create a file named `ssh-key.json` that contains the [necessary payload](https://cloud.lambdalabs.com/api/v1/docs#operation/launchInstance). For example:

    ```json
    {
      "name": "my-new-key",
      "public_key": "ssh-ed25519 KEY COMMENT"
    }
    ```
3.  Run the following command:

    ```bash
    curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/ssh-keys -d @ssh-key.json -H "Content-Type: application/json" | jq .
    ```

Replace **API-KEY** with your actual API key. **Don't remove the trailing colon (:).**

### Generate a new SSH key pair <a href="#generate-a-new-ssh-key-pair" id="generate-a-new-ssh-key-pair"></a>

To generate a new SSH key pair:

1. [Generate an API key](https://cloud.lambdalabs.com/api-keys) if you don’t have one already.
2.  Run the following command:

    ```bash
    curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/ssh-keys -d '{ "name": "my-generated-key" }' -H "Content-Type: application/json" | jq -r '.data.private_key' > my-generated-private-key.pem
    ```

    Replace **API-KEY** with your actual API key. **Don't remove the trailing colon (:).**
3.  The private key for your SSH key pair will be saved as `my-generated-private-key.pem`.

    Run `chmod 400 my-generated-private-key.pem` to set the correct file permissions for your private key.

### List the SSH keys saved in your account <a href="#list-the-ssh-keys-saved-in-your-account" id="list-the-ssh-keys-saved-in-your-account"></a>

To list the SSH keys saved in your account, [generate an API key](https://cloud.lambdalabs.com/api-keys) if you don’t already have one. Then, run the following command:

```bash
curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/ssh-keys | jq .
```

Replace **API-KEY** with your actual API key. **Don’t remove the trailing colon (:).**

### Delete an SSH key from your account <a href="#delete-an-ssh-key-from-your-account" id="delete-an-ssh-key-from-your-account"></a>

To delete an SSH key from your account, [generate an API key](https://cloud.lambdalabs.com/api-keys) if you don’t already have one. Then, run the following command:

```bash
curl -u API-KEY: -X DELETE https://cloud.lambdalabs.com/api/v1/ssh-keys/SSH-KEY-ID
```

Replace **API-KEY** with your actual API key. **Don't remove the trailing colon (:).**

Replace **SSH-KEY-ID** with the ID of the SSH key you want to delete.

{% hint style="info" %}
[Use the API to obtain the IDs of the SSH keys saved in your account](cloud-api.md#list-the-ssh-keys-saved-in-your-account).
{% endhint %}

## Listing file systems

To list your [persistent storage file systems](https://lambdalabs.com/blog/persistent-storage-beta/) using the [Cloud API](https://cloud.lambdalabs.com/api/v1/docs):

1. [Generate an API key](https://cloud.lambdalabs.com/api-keys) if you don’t already have an API key.
2. Run the following command:

```bash
curl -u API-KEY: https://cloud.lambdalabs.com/api/v1/file-systems | jq .
```

Replace **API-KEY** with your actual API key. **Don’t remove the trailing colon (:).**
