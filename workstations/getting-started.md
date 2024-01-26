# Getting started

## How do I set up my workstation?

Instructions for setting up your workstation can be found in our Vector quickstart guide.



{% file src="../.gitbook/assets/Vector_quickstart_guide.pdf" %}
Vector quickstart guide
{% endfile %}

## Where can I download recovery images for my workstation?

Workstation recovery images can be downloaded from our [Lambda Stack and recovery images docs page](../software/lambda-stack-and-recovery-images.md#workstations).

## How do I set the fan speeds for my workstation?

You can set baseline fan speeds for your workstation using `ipmitool`. Once baseline fan speeds are set, you can fine-tune the fan speeds in the web-based IPMI interface.

{% hint style="info" %}
These instructions are only for workstations using an [ASUS Pro WS WRX80E-SAGE SE WIFI](https://www.asus.com/motherboards-components/motherboards/workstation/pro-ws-wrx80e-sage-se-wifi/) motherboard.

Before proceeding with these instructions, run `sudo dmidecode -t 2 | grep Name` to confirm your workstation uses the above motherboard. You should see: `Product Name: Pro WS WRX80E-SAGE SE`.
{% endhint %}

First, install `ipmitool` by running:

```bash
sudo apt -y update && sudo apt -y install ipmitool
```

Then, set the baseline fan speeds by running:

```bash
sudo ipmitool raw 0x30 0x0E 0x04 0x00 0x32 0x23 0x49 0x46 0x5a 0x64 0x61 0x64 0x61 0x64 && \
sudo ipmitool raw 0x30 0x0E 0x04 0x01 0x32 0x23 0x49 0x46 0x5a 0x64 0x61 0x64 0x61 0x64 && \
sudo ipmitool raw 0x30 0x0E 0x04 0x02 0x32 0x23 0x49 0x46 0x5a 0x64 0x61 0x64 0x61 0x64 && \
sudo ipmitool raw 0x30 0x0E 0x04 0x03 0x32 0x23 0x49 0x46 0x5a 0x64 0x61 0x64 0x61 0x64 && \
sudo ipmitool raw 0x30 0x0E 0x04 0x04 0x32 0x23 0x49 0x46 0x5a 0x64 0x61 0x64 0x61 0x64 && \
sudo ipmitool raw 0x30 0x0E 0x04 0x05 0x32 0x23 0x49 0x46 0x5a 0x64 0x61 0x64 0x61 0x64 && \
sudo ipmitool raw 0x30 0x0E 0x04 0x06 0x32 0x23 0x49 0x46 0x5a 0x64 0x61 0x64 0x61 0x64
```

{% hint style="success" %}
See the ASUS ASMB9-iKVM Fan Customized Mode User Guide \[PDF] to learn how to customize fan speeds in the web-based IPMI interface.

Note that Lambda workstations are high-performance systems and generate plenty of heat. For this reason, it's not recommended to use the guide's power efficiency fan policy.
{% endhint %}

{% file src="../.gitbook/assets/ASMB9-iKVM_Fan_Customized_Mode_User_Guide_v0.71_20191112.pdf" %}
ASUS ASMB9-iKVM Fan Customized Mode User Guide
{% endfile %}

## How do I upgrade my Samsung 980 PRO NVMe SSD's firmware?

Follow these instructions to upgrade your Samsung 980 PRO NVMe SSD's firmware.

{% hint style="danger" %}
[Samsung 980 PRO NVMe SSDs with the older 3B2QGXA7 firmware are known to fail](https://www.pugetsystems.com/support/guides/critical-samsung-ssd-firmware-update/).

To know if your SSD is using the 3B2QGXA7 firmware, install the `smartmontools` package by running `sudo apt -y install smartmontools`. Then, run `sudo smartctl -a /dev/nvme0`.

If your SSD is using the 3B2QGXA7 firmware, it's recommended that you upgrade the firmware as soon as possible.
{% endhint %}

First, download the latest firmware ISO from Samsung's website by running:

```bash
wget https://semiconductor.samsung.com/resources/software-resources/Samsung_SSD_980_PRO_5B2QGXA7.iso
```

Next, run `sudo -s` to open a shell with root (administrator) privileges.

Finally, run:

```bash
mkdir /mnt/iso && mount -o loop Samsung_SSD_980_PRO_5B2QGXA7.iso /mnt/iso && \
mkdir fwupdate && cd fwupdate && \
gzip -dc /mnt/iso/initrd | cpio -idv --no-absolute-filenames && \
cd root/fumagician && ./fumagician
```

The above command mounts the firmware upgrade ISO, extracts the firmware upgrade, and launches the upgrade.

After the firmware upgrade completes, restart your computer.

Run `sudo smartctl -a /dev/nvme0` to confirm your SSD is using the new firmware.

## How do I fix slow performance with my Gen 4 M.2 NVMe drive?

There's a known issue where Gen 4 M.2 NVMe drives experience slow performance when installed into the **M.2\_1** slot in ASUS Pro WS WRX80E-SAGE SE WIFI motherboards, which are used in Lambda workstations.

If you run `sudo dmesg | grep -E 'Hardware Error|AER'`, you'll see error messages that look like:

```
[  169.304022] {3}[Hardware Error]: It has been corrected by h/w and requires no further action
[  169.304023] {3}[Hardware Error]: event severity: corrected
[  169.304024] {3}[Hardware Error]:  Error 0, type: corrected
[  169.304025] {3}[Hardware Error]:   section_type: PCIe error
[  169.304026] {3}[Hardware Error]:   port_type: 0, PCIe end point
[  169.304026] {3}[Hardware Error]:   version: 0.2
[  169.304027] {3}[Hardware Error]:   command: 0x0406, status: 0x0010
[  169.304028] {3}[Hardware Error]:   device_id: 0000:2c:00.0
[  169.304029] {3}[Hardware Error]:   slot: 0
[  169.304029] {3}[Hardware Error]:   secondary_bus: 0x00
[  169.304030] {3}[Hardware Error]:   vendor_id: 0x1022, device_id: 0xb000
[  169.304030] {3}[Hardware Error]:   class_code: 010802
[  169.304031] {3}[Hardware Error]:   bridge: secondary_status: 0x0000, control: 0x0000
```

The error messages might also look like:

```
[    4.172130] acpi PNP0A08:03: PCIe AER handled by firmware
[   59.749158] nvme 0000:2c:00.0: AER: aer_status: 0x00002001, aer_mask: 0x00000000
[   59.749860] nvme 0000:2c:00.0: AER:	  [ 0] RxErr		      (First)
[   59.750522] nvme 0000:2c:00.0: AER:	  [13] NonFatalErr
[   59.751161] nvme 0000:2c:00.0: AER: aer_layer=Physical Layer, aer_agent=Receiver ID
```

If you're experiencing slow performance and seeing errors, [contact Lambda Support](https://support.lambdalabs.com/hc/en-us/requests/new) for a BIOS update that fixes the issue.

## Can I upgrade my workstation to RTX 4090 GPUs?

Workstations can't be upgraded to RTX 4090 GPUs.

To ensure system stability and longevity, the RTX 4090 GPUs we use in our workstations are liquid-cooled, as opposed to air-cooled like other GPUs. To accommodate the liquid-cooling solution and dissipate the amount of heat put out by the RTX 4090 GPUs, the workstation case requires special fan designs and layouts.
