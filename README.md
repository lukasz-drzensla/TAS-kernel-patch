# TAS-kernel-patch
Linux kernel patch developed for my bachelor of engineering degree. Patch introduces modifications to Con Kolivas' MuQSS scheduler and coretemp driver for temperature aware scheduling.

TAS introduces a scheduling strategy which uses current CPU core temperatures obtained from coretemp driver to hint the MuQSS which cores are suitable for running new tasks. TAS replaces the default strategy of setting cores as idle with a new one which states that the coolest core is idle. This is an expermental approach to achieve temperature aware scheduling.

This patch is provided under the same license as the Linux kernel as described in the COPYING file.

MuQSS by Con Kolivas can be found here: http://ck.kolivas.org/patches/muqss/

# Kernel version support
Only kernel version 5.12 with MuQSS 5.12 has been tested.

# Hardware support
All CPUs supported by coretemp driver are supported. Tested only with i7-3632QM.

# Cloning
As files provided in this repo do not form a standalone project, cloning strategy is irrelevant. You may as well download the files as a zip file.

# Applying patch
If you already have Linux kernel sources with applied MuQSS scheduler, you may only apply the TAS.patch file. To do so cd to the main kernel sources directory and execute the following command:
```bash
patch -p1 < [path_to_parent]/TAS.patch
```
Replace [path_to_parent] with the directory in which you have placed TAS.patch file.

If you don't have kernel sources with MuQSS applied, you can use TAS-MuQSS.patch file to apply both MuQSS scheduler patch and TAS strategy patch at once. To do so cd to the main kernel sources directory and execute:
```bash
patch -p1 < [path_to_parent]/TAS-MuQSS.patch
```
Replace [path_to_parent] with the directory in which you have placed TAS-MuQSS.patch file.

# Building
In order to build the kernel with the patch applied follow the same procedures as if no patch was applied. If your sources don't interfere with patches, the kernel should compile with no errors.
