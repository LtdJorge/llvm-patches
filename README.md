# sys-devel/llvm patches

## Background
Building the kernel with LLVM=1 crashes LLD with LLVM >= 18 **when using -march=znver{1,2,3,4,5}**

The relevant issue is llvm/llvm-project#82431

These patches correspond to two PRs: llvm/llvm-project#82881 and llvm/llvm-project#85081. The first one is already merged to main branch, the second isn't. These patches are just the two commits from the pull requests cherry-picked on the 18.1.5 and 18.1.6 tags.

## How to apply the patches
Applying the patches is as easy as:

First, create the patches directory for your version of llvm:
```shell
sudo mkdir -p /etc/portage/patches/sys-devel/llvm-18.1.6
```

Clone the repo:
```shell
git clone https://github.com/LtdJorge/llvm-patches.git llvm-patches
```

Then, copy the relevant ones to said directory:
```shell
sudo cp llvm-patches/18-1-6/* /etc/portage/patches/sys-devel/llvm-18.1.6/
```

After that, reemerge llvm (no need to reemerge Clang, LLD, etc):
```shell
sudo emerge -av llvm
```

Finally, rebuild your kernel with `LLVM=1` with your standard procedure

## Tested llvm versions and kernels
This has been tested working with llvm-18.5.5-r1 and llvm-18.1.6. The tested kernel is sys-kernel/gentoo-sources version 6.9.0, but any kernel should do, as long as it's compiled with any AMD Zen Arch and LLVM=1.
