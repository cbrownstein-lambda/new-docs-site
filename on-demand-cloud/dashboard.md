# Dashboard

The [dashboard](https://cloud.lambdalabs.com/instances) makes it easy to get started using Lambda GPU Cloud.

From the dashboard, you can:

* [Launch, restart, and terminate instances](dashboard.md#launch-restart-and-terminate-instances).
* [Create and manage persistent storage file systems](dashboard.md#create-and-manage-persistent-storage-file-systems).
* [Add, generate, and delete SSH keys](dashboard.md#add-generate-and-delete-ssh-keys).
* [Generate and delete API keys](dashboard.md#generate-and-delete-api-keys).
* [Use the Demos feature](dashboard.md#use-the-demos-feature).
* [View usage](dashboard.md#view-usage).
* [Manage a Team](dashboard.md#manage-a-team).
* [Modify account settings](dashboard.md#modify-account-settings).

## Launch, restart, and terminate instances <a href="#launch-restart-and-terminate-instances" id="launch-restart-and-terminate-instances"></a>

### Launch instances <a href="#launch-instances" id="launch-instances"></a>

To launch an instance:

1.  Click [**Instances**](https://cloud.lambdalabs.com/instances) in the left sidebar of the dashboard.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/dashboard-sidebar_hu9ecb6b1ffbbdab44f0031994b36281b3_10636_200x0_resize_catmullrom_3.png" alt="" height="601" width="200"><figcaption></figcaption></figure>

    Then, click **Launch instance** at the top-right of the dashboard.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/launch-instance-button_hu72e9fb331bce1462e8a1c859cbc5f3a4_3103_200x0_resize_catmullrom_3.png" alt="" height="138" width="200"><figcaption></figcaption></figure>
2.  Click the instance type that you want to launch.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/launch-instance-type_hub851226451de6ed184c03482abaa8554_73188_400x0_resize_catmullrom_3.png" alt="" height="646" width="400"><figcaption></figcaption></figure>
3.  Click the region in which you want to launch the instance.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/select-region_hu1c84697aa3f6ddd66722dec058349f8d_48366_400x0_resize_catmullrom_3.png" alt="" height="603" width="400"><figcaption></figcaption></figure>
4.  Click the [persistent storage file system](dashboard.md#create-and-manage-persistent-storage-file-systems) that you want to attach to your instance.

    If you don’t want to or can’t attach a persistent storage file system to your instance, click **Don’t attach a filesystem**.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/select-filesystem_hue77a61cb97978d55e3dfab52056fd4fe_26306_400x0_resize_catmullrom_3.png" alt="" height="287" width="400"><figcaption></figcaption></figure>
5.  Select the [SSH key](dashboard.md#add-generate-and-delete-ssh-keys) that you want to use for your instance. Then, click **Launch instance**.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/select-ssh-key_hu06e4a428bfa7d423474ce5f89c1d936f_18010_400x0_resize_catmullrom_3.png" alt="" height="274" width="400"><figcaption></figcaption></figure>

{% hint style="success" %}
You can [add additional SSH keys](getting-started.md#zd-article-title) to your instance once your instance has launched.
{% endhint %}

1.  Review the license agreements and terms of service. If you agree to them, click **I agree to the above** to launch your instance.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/licensing-agreements_hu5af0173f75998de08196db51ee4d2b3a_31686_400x0_resize_catmullrom_3.png" alt="" height="274" width="400"><figcaption></figcaption></figure>

In the dashboard, you should now see your instance listed. Once your instance has finished booting, you’ll be provided with the details needed to begin using your instance.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/instance-details_hu4c7417e3176dcc62a689d5e423bc65a4_14519_1000x0_resize_catmullrom_3.png" alt="" height="58" width="1000"><figcaption></figcaption></figure>

{% hint style="success" %}
You can also [launch instances using the Cloud API](cloud-api.md#launching-instances).

You can also use the Cloud API to [get details of a running instance](cloud-api.md#getting-details-of-a-specific-instance).
{% endhint %}

### Restart instances <a href="#restart-instances" id="restart-instances"></a>

Restart instances by clicking the checkboxes next to the instances you want to restart. Then, click **Restart** at the top-right of the dashboard.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/restart-terminate_hud627d239c4da9ede8a38f23f49943247_5199_300x0_resize_catmullrom_3.png" alt="" height="83" width="300"><figcaption></figcaption></figure>

### Terminate instances <a href="#terminate-instances" id="terminate-instances"></a>

Terminate instances by clicking the checkboxes next to the instances you want to terminate. Then, click **Terminate** at the top-right of the dashboard.

When prompted to do so, type in **erase data on instance**, then click **Terminate instances**.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/restart-terminate_hud627d239c4da9ede8a38f23f49943247_5199_300x0_resize_catmullrom_3.png" alt="" height="83" width="300"><figcaption></figcaption></figure>

{% hint style="success" %}
You can also [terminate instances using the Cloud API](https://docs.lambdalabs.com/cloud/terminate-instance-api/).
{% endhint %}

### Create and manage persistent storage file systems <a href="#create-and-manage-persistent-storage-file-systems" id="create-and-manage-persistent-storage-file-systems"></a>

#### Create a persistent storage file system <a href="#create-a-persistent-storage-file-system" id="create-a-persistent-storage-file-system"></a>

To create a persistent storage file system:

1.  Click [**Storage**](https://cloud.lambdalabs.com/file-systems) in the left sidebar of the dashboard.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/dashboard-sidebar_hu9ecb6b1ffbbdab44f0031994b36281b3_10636_200x0_resize_catmullrom_3.png" alt="" height="601" width="200"><figcaption></figcaption></figure>

    Then, click **Create filesystem** at the top-right of the dashboard.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/create-filesystem-button_hu4bc2ae563fd966da9dcbd0716cf5bea9_3054_200x0_resize_catmullrom_3.png" alt="" height="138" width="200"><figcaption></figcaption></figure>
2.  Enter a name and select a region for your file system. Then click **Create filesystem**.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/create-filesystem_hu0262777a553524f8bb9cf2204e87b563_16148_400x0_resize_catmullrom_3.png" alt="" height="248" width="400"><figcaption></figcaption></figure>

You should now see your persistent storage file system listed in the dashboard.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/persistent-storage-details_hu771c863def9e82a3a98482082803fd9a_10534_800x0_resize_catmullrom_3.png" alt="" height="138" width="800"><figcaption></figcaption></figure>

### Add, generate, and delete SSH keys <a href="#add-generate-and-delete-ssh-keys" id="add-generate-and-delete-ssh-keys"></a>

#### Add or generate an SSH key <a href="#add-or-generate-an-ssh-key" id="add-or-generate-an-ssh-key"></a>

To add an SSH key that you already have:

1.  Click [**SSH keys**](https://cloud.lambdalabs.com/ssh-keys) in the left sidebar of the dashboard.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/dashboard-sidebar_hu9ecb6b1ffbbdab44f0031994b36281b3_10636_200x0_resize_catmullrom_3.png" alt="" height="601" width="200"><figcaption></figcaption></figure>

    Then, click **Add SSH key** at the top-right of the dashboard.
2. In the text input box, paste your public SSH key. Enter a name for your key, then click **Add SSH key**.

To generate a new SSH key:

1.  Instead of pasting your public SSH key as instructed, above, click **Generate a new SSH key**. Type in a name for your key, then click **Create**.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/generate-new-ssh-key_hu3771dfde09553cca1a414dff27eb8bb6_11313_400x0_resize_catmullrom_3.png" alt="" height="210" width="400"><figcaption></figcaption></figure>

    The private key for your new SSH key will automatically download.

{% hint style="success" %}
You can also [use the Cloud API to add and generate SSH keys](cloud-api.md#add-an-existing-ssh-key-to-your-account).
{% endhint %}

#### Delete SSH keys <a href="#delete-ssh-keys" id="delete-ssh-keys"></a>

Delete SSH keys by clicking **Delete** at the far-right of the SSH key you want to delete.

### Generate and delete API keys <a href="#generate-and-delete-api-keys" id="generate-and-delete-api-keys"></a>

#### Generate API keys <a href="#generate-api-keys" id="generate-api-keys"></a>

Generate API keys by clicking [**API keys**](https://cloud.lambdalabs.com/api-keys) in the left sidebar of the dashboard.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/dashboard-sidebar_hu9ecb6b1ffbbdab44f0031994b36281b3_10636_200x0_resize_catmullrom_3.png" alt="" height="601" width="200"><figcaption></figcaption></figure>

Then, click **Generate API Key** at the top-right of the dashboard.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/generate-api-key-button_hu07d0130472ff3814cbf8a8f1a2ef4796_1179_200x0_resize_catmullrom_3.png" alt="" height="76" width="200"><figcaption></figcaption></figure>

#### Delete API keys <a href="#delete-api-keys" id="delete-api-keys"></a>

Delete API keys by clicking **Delete** at the far-right of the API key you want to delete.

### Use the Demos feature <a href="#use-the-demos-feature" id="use-the-demos-feature"></a>

Use the Demos feature by clicking [**Demos**](https://cloud.lambdalabs.com/edit-demos) in the left sidebar of the dashboard.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/dashboard-sidebar_hu9ecb6b1ffbbdab44f0031994b36281b3_10636_200x0_resize_catmullrom_3.png" alt="" height="601" width="200"><figcaption></figcaption></figure>

### View usage <a href="#view-usage" id="view-usage"></a>

View usage information by clicking [**Usage**](https://cloud.lambdalabs.com/usage) in the left sidebar of the dashboard.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/dashboard-sidebar_hu9ecb6b1ffbbdab44f0031994b36281b3_10636_200x0_resize_catmullrom_3.png" alt="" height="601" width="200"><figcaption></figcaption></figure>

### Manage a Team <a href="#manage-a-team" id="manage-a-team"></a>

Click [**Team**](https://cloud.lambdalabs.com/team) at the bottom of the left sidebar to access the Team feature.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/sidebar-team-settings_hu8f0c5ee5793f3637eb302241374875ec_2792_100x0_resize_catmullrom_3.png" alt="" height="62" width="100"><figcaption></figcaption></figure>

Learn how to manage a Team by reading our FAQ on [getting started with the Team feature](https://docs.lambdalabs.com/cloud/get-started-teams/).

### Modify account settings <a href="#modify-account-settings" id="modify-account-settings"></a>

Click [**Settings**](https://cloud.lambdalabs.com/settings) at the bottom of the left sidebar to modify your account settings, including your password and payment method.

<figure><img src="https://old.docs.lambdalabs.com/cloud/cloud-dashboard/sidebar-team-settings_hu8f0c5ee5793f3637eb302241374875ec_2792_100x0_resize_catmullrom_3.png" alt="" height="62" width="100"><figcaption></figcaption></figure>
