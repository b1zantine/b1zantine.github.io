---
layout: post
title: "Installing Nvidia CUDA Toolkit and drivers in Ubuntu 14.04 / 16.04"
description: "A guide to install Nvidia drivers and CUDA in Ubuntu, the right way for Deep Learning"
categories: cuda ubuntu
---

Setting up Nvidia CUDA toolkit along with the drivers in Ubuntu for the purpose of training
your deep learning models can give you quite the headache if proper instructions are
not followed during installation.

This installation guide is written with the assumption that you have a fresh copy of
Ubuntu 14.04 or 16.04 installed in your system and has no login problems. You don't even have to install the Nvidia drivers beforehand.

>If you have already tried installing the Nvidia driver using the command similar to
>`sudo apt-get install nvidia-352` , then you might probably have to follow the
>instructions given in this <a href="http://askubuntu.com/a/163808/607113" target="_blank">link</a>
>to remove it before proceeding.

###### Pre-install checklist
- Check whether you have a CUDA capable Nvidia graphics card using `lspci | grep -i nvidia`
- Download the CUDA runfile from <a href="https://developer.nvidia.com/cuda-downloads" target='_blank'>here</a>. File may have a name similar to `cuda_8.0.44_linux.run`.
- Also run `sudo apt-get install build-essential`

###### Instructions

1. Remove the `xorg.conf` file using `sudo rm /etc/X11/xorg.conf`

2. Create the file `/etc/modprobe.d/blacklist-nouveau.conf` and add the following lines to it
```
blacklist nouveau
options nouveau modeset=0
```
Then, do `sudo update-initramfs -u`

3. Reboot your computer. Nothing should have changed in loading up menu. You should be taken to the login screen. Once there, press <kbd>Ctrl + Alt + F1</kbd> and login to your user.

4. Go to the directory where you have the CUDA file and run `chmod a+x`

5. Now, run `sudo service lightdm stop`. This step is required for installing
the driver successfully.

6. Run the CUDA driver runfile using `sudo bash cuda_8.0.44_linux.run --no-opengl-libs`. Notice that here it is explicitly mentioned not to install the **OpenGL libraries**. Otherwise this may cause **login loops**.

7. During the installation,
- Accept EULA conditions
- Say YES to installing the NVIDIA driver
- Say YES to installing CUDA Toolkit + Driver
- Say YES to installing CUDA Samples
- Say <mark>NO</mark> to rebuilding any Xserver configurations with Nvidia

8. After the installation is completed, check if device nodes are present:
Check if `/dev/nvidia*` files exist. If they don't, then do `sudo modprobe nvidia`

9.  Set Environment path variables:  
```bash
echo "export PATH=/usr/local/cuda/bin:$PATH" >> ~/.bashrc
echo "export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH" >> ~/.bashrc
source ~/.bashrc
```

10. Verify the driver version: `cat /proc/driver/nvidia/version`

11. Check CUDA driver version: `nvcc -V`

12. [Optional] At this point you can switch the lightdm back on again by doing:
`sudo service lightdm start`.
You should be able to login to your session through the GUI without any problems or login-loops.

13. Create CUDA Samples. Go to your NVIDIA_CUDA-8.0_Samples folder and run `make`.

14. Go to `NVIDIA_CUDA-8.0_Samples/bin/x86_64/linux/release/` for the demos, and do the two standard checks:
```bash
./deviceQuery
```
to see your graphics card specifications and
```bash
./bandwidthTest
```
to check if its operating correctly.
Both tests should ultimately output a **'PASS'** in your terminal.

15. Reboot. It should boot normally.

Thats it. You have successfully installed the Nvidia CUDA toolkit and the necessary drivers for
training your deep learning models.
