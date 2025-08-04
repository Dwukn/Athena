# Athena 

This repository contains my **custom Linux kernel `.config` file**, tailored specifically for **my hardware setup**. This project was created as part of my journey to learn Linux kernel development and experimentation. **Currently, only the config file is shared**, since the actual compiled kernel may cause system instability if used on non-compatible machines.

> [!IMPORTANT] 
> This config is **hardware-specific** and **not meant for general use**. If you use this without understanding the risks, you may break your system. Proceed only if you know what you’re doing or you're just exploring the config for educational purposes.

---

## 📚 Why this repo?

- To learn Linux kernel internals and compilation
- To experiment with kernel configuration, patching, and build systems
- To maintain a versioned backup of my kernel config

---

## 🧠 What’s in this repo?

- `.config`: The kernel configuration file generated via `make menuconfig` and customized for my system.

---

## 🔧 How to Build the Kernel (for first-time users)

> [!NOTE]
> 🧠 These steps assume you are running on an **Arch Linux** or similar system with basic development tools installed.

### 1. Install required packages

```bash
sudo pacman -S base-devel ncurses git bc kmod libelf openssl zstd cpio perl
```

2. Clone the official Linux kernel source

```bash
git clone https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
cd linux
```

3. Copy the provided config file

``` bash
cp /path/to/this/repo/.config .config
```

> [!Note]
    ⚠️ This config is designed for my hardware. You may need to tweak it using "make menuconfig" or "make nconfig" to suit your system.

4. Compile the kernel

```
make -j$(nproc)
```

> [!Note]
>  nproc outputs number of cores your cpu have so `make -j$(nproc)` will use all your cores so using your system may not be the best idea, you can also do `make -j<number>` the <number> tell compiler use these many cores lowest is 1 and max is number of cores your cpu have,
> Higher number means faster compilation times 

5. Install the modules

```
sudo make modules_install
```

6. Install the kernel

```
sudo make install
```

This will place the kernel image and initramfs in /boot and update your bootloader entries automatically if you're using something like GRUB.

> [!IMPORTANT]
> This repo is not intended to distribute a generic kernel.
> Always backup your system or work in a VM before testing a custom kernel.
> If you're new to kernel dev, check out resources like Linux Kernel Newbies or LWN.net.
>

## 📚 Resources to Learn Kernel Development

- [Kernel Newbies](https://kernelnewbies.org/)  
  A community and set of resources for new Linux kernel developers.

- [LWN.net Kernel Index](https://lwn.net/Kernel/)  
  Detailed articles and updates on Linux kernel development.

- [The Linux Kernel Archives](https://www.kernel.org/)  
  The primary site for the Linux kernel source, releases, and changelogs.

- [Linux Kernel Development (Robert Love) – PDF](https://www.doc-developpement-durable.org/file/Projets-informatiques/cours-&-manuels-informatiques/Linux/Linux%20Kernel%20Development,%203rd%20Edition.pdf)  
  A widely recommended book for learning Linux kernel internals.

- [Linux Kernel Teaching (by @xairy)](https://xairy.io/trainings/)  
  A collection of training materials and tutorials for understanding the Linux kernel.
