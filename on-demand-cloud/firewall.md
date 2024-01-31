# Firewall

The [Firewall feature](https://cloud.lambdalabs.com/firewall) allows you to configure firewall rules to restrict incoming traffic to your instances.

Firewall rules configured using the Firewall feature apply to all of your instances outside of the Texas, USA (us-south-1) region.

To use the Firewall feature:

1.  Click **Firewall** in the left sidebar of the dashboard to open your firewall settings.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/get-started-firewall/firewall-settings_hu5a2391b21be25c5c402ce93aab8d4fa4_32076_400x0_resize_catmullrom_3.png" alt="" height="406" width="400"><figcaption></figcaption></figure>

    Under **General Settings**, use the toggle next to **Allow ICMP traffic (ping)** to allow or restrict incoming ICMP traffic to your instances.

    **Note**

    For network diagnostic tools such as `ping` and `mtr` to be able to reach your instances, you need to allow incoming ICMP traffic.
2.  Next to **Inbound Rules**, click **Edit** to configure incoming TCP and UDP traffic rules.

    <figure><img src="https://old.docs.lambdalabs.com/cloud/get-started-firewall/inbound-rules_hu57237b4cb7c6773609764b2590b570c8_17437_800x0_resize_catmullrom_3.png" alt="" height="312" width="800"><figcaption></figcaption></figure>

    In the drop-down menu under **Type**, select:

    * **Custom TCP** to manually configure a rule to allow incoming TCP traffic.
    * **Custom UDP** to manually configure a rule to allow incoming UDP traffic.
    * **HTTPS** to automatically configure a rule to allow incoming HTTPS traffic.
    * **SSH** to automatically configure a rule to allow incoming SSH traffic.
    * **All TCP** to automatically configure a rule to allow all incoming TCP traffic.
    * **All UDP** to automatically configure a rule to allow all incoming UDP traffic.

    **Warning**

    If you don’t have a rule to allow incoming traffic to port TCP/22, **you won’t be able to access your instances using SSH**.

    In the **Source** field, either:

    * Click the 🔎 to automatically enter your current IP address.
    * Enter a single IP address, for example, `203.0.113.1`.
    * Enter an IP address range in CIDR notation, for example, `203.0.113.0/24`.

    To allow incoming traffic from any source, enter `0.0.0.0/0`.

    If you choose **Custom TCP** or **Custom UDP**, enter a **Port range**.

    **Port range** can be:

    * A single port, for example, `8080`.
    * A range of ports, for example, `8080-8081`.
3. (Optional) Enter a **Description** for the rule.
4. (Optional) Click **Add rule** to add additional rules.
5. (Optional) Click the x next to any rule you want to delete.
6. Click **Update** to apply your changes.

{% hint style="info" %}
The maximum number of firewall rules you can have is 20.

If you have more than 20 rules, new instances you create might not launch. Also, it’s possible that not all of your rules will be active, which might leave your instances unsecure.
{% endhint %}
