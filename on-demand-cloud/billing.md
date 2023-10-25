# Billing

## How are on-demand instances billed?

[On-demand instances](https://lambdalabs.com/service/gpu-cloud) are billed in one-minute increments from the moment you spin up (start) the instance up to the moment you terminate (stop) the instance.

{% hint style="danger" %}
Be sure to terminate any instances that you’re not using!

**You will be billed for all minutes that an instance is running, even if the instance isn’t actively being used.**
{% endhint %}

The GPU Cloud dashboard allows you to [view your resource usage](https://cloud.lambdalabs.com/usage).

Invoices are sent weekly for the previous week's usage.

{% hint style="info" %}
On-demand instances require us to maintain excess capacity at all times so we can meet the changing workloads of our customers. For this reason, on-demand instances are priced higher than reserved instances.

Conversely, we offer [reserved GPU Cloud instances](https://lambdalabs.com/service/gpu-cloud/reserved) at a significant savings over on-demand instances, since they allow us to more accurately determine our capacity needs ahead of time.
{% endhint %}

## How are file systems billed?

File systems are billed per GB used per month, in increments of 1 hour.

For example, based on the price of $0.20 per GB used per month:

* If you use 1,000 GB of your file system capacity for an entire month (30 days, or 720 hours), you'll be billed $200.00.
* If you use 1,000 GB of your file system capacity for a single day (24 hours), you'll be billed $6.67.

{% hint style="info" %}
The actual price of persistent storage will be displayed when you create your file system.
{% endhint %}

## Why is my card being declined?

Common reasons why card transactions are declined include:

### The card is a prepaid card or debit card

We don't accept debit cards or prepaid cards. We only accept major credit cards.

### The purchase is being made from a country we don't support

We currently only support customers in the following regions:

* United States
* Canada
* Chile
* Iceland
* United Arab Emirates
* Saudi Arabia
* South Africa
* Israel
* Taiwan
* South Korea
* Japan
* Singapore
* Australia
* New Zealand
* United Kingdom
* Switzerland
* European Union

### The purchase is being made while you're connected to a VPN

Purchases made while using a VPN are flagged as suspicious.

### The card issuer is denying our pre-authorization charge

We make a $10 pre-authorization charge to a card before accepting it for payment, similar to how gas stations and hotels do. If the card issuer denies the pre-authorization charge, then we can't accept the card for payment.

### Wrong CVV or ZIP Code is being entered

Card purchases won't go through if the CVV (security code) is entered incorrectly. Also, card purchases will be denied if the ZIP Code doesn't match with the card billing address.

If none of these are applicable to you, [contact the Lambda Support team](https://support.lambdalabs.com/hc/en-us/requests/new) for help.

## What happens to my account if I don't pay an invoice?

{% hint style="danger" %}
If an [invoice](billing.md#zd-article-title) remains unpaid after we've made 4 attempts to charge the card on file, we may suspend your account.

If your account is suspended, your running instances may be terminated and your files may be deleted without prior notice.

Eventually, all of your instances will be terminated and all of your [persistent storage file systems](https://docs.lambdalabs.com/cloud/use-persistent-storage/) will be deleted.

Your account will be permanently banned from Lambda GPU Cloud. Your account will be referred for collection. Legal action may be taken against you.
{% endhint %}

## How are refunds given?

Refunds are given in the form of credit toward future Cloud usage only. The credit can't be redeemed for cash (for example, refund to a card) and can't be used toward purchases of other Lambda products.

The credit expires 12 months after it is given.

The credit is nontransferable and is subject to the [Lambda Cloud Terms of Service](https://lambdalabs.com/legal/terms-of-service#cloud-terms-of-service).

## Can you provide an estimate of how much a job will cost?

We can't estimate how much your job will cost or how long it'll take to complete on one of our instances. This is because we don't know the details of your job, such as how your program works.

However, the performance of our instances is close to what you'd expect from bare metal machines with the same GPUs.

In order to estimate how much your job will cost or how long it'll take to complete, we suggest you create an instance and benchmark your program.

{% hint style="success" %}
[Check out our GPU benchmarks](https://lambdalabs.com/gpu-benchmarks) to form a general idea of the performance provided by our instances. Keep in mind that real-world performance doesn't always match the performance provided by benchmarks.

For help benchmarking or optimizing your ML jobs, [contact our Machine Learning team](https://lambdalabs.com/professional-services).
{% endhint %}

