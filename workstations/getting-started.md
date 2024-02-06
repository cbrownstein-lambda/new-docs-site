# Getting started

## How do I set up my workstation?

Instructions for setting up your [Vector](https://lambdalabs.com/gpu-workstations/vector) can be found in our Vector quickstart guide.

Instructions for setting up your [Vector One](https://lambdalabs.com/gpu-workstations/vector-one) can be found in our Vector One quickstart guide.

{% file src="../.gitbook/assets/Vector_quickstart_guide.pdf" %}
Vector quickstart guide
{% endfile %}

{% file src="../.gitbook/assets/Lambda Vector One Quick Start Guide.pdf" %}
Vector One quickstart guide
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

## What are the power requirements for my workstation's PSU?

{% hint style="danger" %}
Lambda workstations are high-performance systems and use a large amount of power. For this reason, **Lambda workstations can’t reliably be used with uninterruptible power supplies (UPSs, or battery backups)**.

If you use a UPS with your workstation, you might experience system instability and trouble booting.
{% endhint %}

The power requirements for Lambda workstation power supply units (PSUs) are as follows:

{% hint style="info" %}
The manufacturer and model of your workstation’s PSU appears on the label on the PSU.
{% endhint %}

| Manufacturer | Model             | Wattage | Voltage (AC) | Current (A) | Frequency (Hz) | Inlet/Outlet |
| ------------ | ----------------- | ------- | ------------ | ----------- | -------------- | ------------ |
| Super Flower | SF-1300F14MG V1.0 | 1300    | 100-240      | 15          | 60/50          | C14/C13      |
| Super Flower | SF-1600F14HT      | 1600    | 115-240      | 17-10       | 60/50          | C20/C19      |
| Super Flower | SF-2000F14HP      | 2000    | 200-240      | 15          | 50             | C20/C19      |

### Power connector inlets and outlets <a href="#power-connector-inlets-and-outlets" id="power-connector-inlets-and-outlets"></a>

This is what a **C14 inlet** looks like:

<figure><img src="https://old.docs.lambdalabs.com/workstations/power-requirements/c14-inlet_hu736c83625d865319dbb7c46a0c4cd646_228543_200x0_resize_catmullrom_3.png" alt="" height="216" width="200"><figcaption></figcaption></figure>

This is what a **C13 outlet** looks like:

<figure><img src="https://old.docs.lambdalabs.com/workstations/power-requirements/c13-outlet_hud56b78fe4bc7f393914f8df1a5e81f80_12059_200x0_resize_catmullrom_3.png" alt="" height="181" width="200"><figcaption></figcaption></figure>

This is what a **C20 inlet** looks like:

<figure><img src="https://old.docs.lambdalabs.com/workstations/power-requirements/c20-inlet_hu59d9cac5d3c364ee3122d4d7185ecd7c_39408_200x0_resize_catmullrom_3.png" alt="" height="205" width="200"><figcaption></figcaption></figure>

This is what a **C19 outlet** looks like:

<figure><img src="https://old.docs.lambdalabs.com/workstations/power-requirements/c19-outlet_hu79a2640a08ec511198f30587dd9704ba_8872_200x0_resize_catmullrom_3.png" alt="" height="208" width="200"><figcaption></figcaption></figure>

### Power cord plugs and receptacles <a href="#power-cord-plugs-and-receptacles" id="power-cord-plugs-and-receptacles"></a>

{% hint style="danger" %}
Lambda workstations **must** be connected to a dedicated power circuit that isn’t shared with other devices. Otherwise, the **breaker will trip and disconnect power to the circuit**.
{% endhint %}

#### SF-1300F14MG V1.0 1300W PSU <a href="#sf-1300f14mg-v10-1300w-psu" id="sf-1300f14mg-v10-1300w-psu"></a>

For customers in North America, the SF-1300F14MG V1.0 1300W PSU power cord has a NEMA 5-15 plug. The plug inserts into NEMA 5-15 and NEMA 5-20 receptacles, which look like this:

<figure><img src="https://old.docs.lambdalabs.com/workstations/power-requirements/20A-15A-outlets_hue54a9df8979ad81fb35fe71aacc99e09_218903_400x0_resize_catmullrom_3.png" alt="" height="213" width="400"><figcaption></figcaption></figure>

On request, a C13-C14 power cord can be substituted for use with power distribution units (PDUs) commonly found in data centers.

#### SF-1600F14HT 1600W PSU <a href="#sf-1600f14ht-1600w-psu" id="sf-1600f14ht-1600w-psu"></a>

For customers in North America, the SF-1600F14HT 1600W PSU power cord uses a NEMA 5-20 plug. The plug inserts into a NEMA 5-20 receptacle, which looks like the receptacle on the right in the picture, below.

<figure><img src="https://old.docs.lambdalabs.com/workstations/power-requirements/20A-15A-outlets_hue54a9df8979ad81fb35fe71aacc99e09_218903_400x0_resize_catmullrom_3.png" alt="" height="213" width="400"><figcaption></figcaption></figure>

On request, a C19-C20 power cord can be substituted for use with power distribution units (PDUs) commonly found in data centers.

#### SF-2000F14HP 2000W PSU <a href="#sf-2000f14hp-2000w-psu" id="sf-2000f14hp-2000w-psu"></a>

For customers in North America, the SF-2000F14HP 2000W PSU power cord uses NEMA 6-20 or NEMA 6-15 connectors, which look like the ones in the third row in the picture, below.

<figure><img src="https://old.docs.lambdalabs.com/workstations/power-requirements/NEMA-connectors_hu4996818b1a6cb5a7fddb62337e57667c_59925_400x0_resize_catmullrom_3.png" alt="" height="330" width="400"><figcaption></figcaption></figure>

On request, a C19-C20 power cord can be substituted for use with power distribution units (PDUs) commonly found in data centers.

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
