# Lambda Stack and recovery images

## Packages included in Lambda Stack

<!-- TODO: List packages included in Lambda Stack, and their versions. -->

## Removing and reinstalling Lambda Stack

To remove and reinstall [Lambda Stack](https://lambdalabs.com/lambda-stack-deep-learning-software):

Uninstall (purge) the existing Lambda Stack by running:

```bash
sudo rm -f /etc/apt/sources.list.d/{graphics,nvidia,cuda}* && \
dpkg -l | \
awk '/cuda|lib(accinj64|cu(blas|dart|dnn|fft|inj|pti|rand|solver|sparse)|magma|nccl|npp|nv[^p])|nv(idia|ml)|tensor(flow|board)|torch/ { print $2 }' | \
sudo xargs -or apt -y remove --purge
```

Then, install the latest Lambda Stack by running:

```bash
wget -nv -O- https://lambdalabs.com/install-lambda-stack.sh | sh -
```

## Recovery images

### Workstations

Recovery ISO images for [Vector](https://lambdalabs.com/gpu-workstations/vector) can be downloaded using the following links:

* [Lambda Recovery (Focal)](https://files.lambdalabs.com/recovery/lambda-recovery-focal-20230704.iso) (based on Ubuntu 20.04 LTS _focal_)
* [Lambda Recovery (Jammy)](https://files.lambdalabs.com/recovery/lambda-recovery-jammy-20230704.iso) (based on Ubuntu 22.04 LTS _jammy_)

### Tensorbook

The recovery ISO image for [Tensorbook](https://lambdalabs.com/deep-learning/laptops/tensorbook) can be downloaded using the following link:

* [Lambda Recovery for Tensorbook (Jammy)](https://files.lambdalabs.com/recovery/tensorbook-jammy-20230704.iso) (based on Ubuntu 22.04 LTS _jammy_)

{% hint style="info" %}
This recovery image is for the _Razer x Lambda Tensorbook_ only and won't work on older Tensorbook models.
{% endhint %}

{% hint style="info" %}
The recovery images contain software distributed under various licenses, including the [Software License Agreement (SLA) for NVIDIA cuDNN](https://docs.nvidia.com/deeplearning/cudnn/sla/index.html). The licenses can be viewed in the recovery images at `/usr/share/doc/*/copyright`. By using the software contained in the recovery images, you agree to these licenses.
{% endhint %}

