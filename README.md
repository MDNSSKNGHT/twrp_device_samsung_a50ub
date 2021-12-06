# Recovery Device Tree for SM-A505G (Galaxy A50)

## How to compile
For compiling, you need three components, [device tree](https://github.com/MDNSSKNGHT/twrp_device_samsung_a50ub), [kernel sources](https://github.com/MDNSSKNGHT/android_kernel_samsung_a50ub), and [toolchains](https://github.com/MDNSSKNGHT/toolchains-exynos9610).

Procedure is simple, but before we continue, your folder layout should look like this.

    <recovery sources>/device/samsung/a50ub
                    -> <the files of this repository>

    <recovery sources>/kernel/samsung/a50ub
                    -> <the files of the kernel repository>

    <user home>/toolchains-exynos9610/
                    -> <the files of the toolchains repository>

After you've set the repositories path, we can go ahead, execute the following commands in your shell.

    source $HOME/toolchains-exynos9610/export.sh
    export CROSS_COMPILE=aarch64-linux-android-
    export CC=clang
    export CLANG_TRIPLE=aarch64-linux-gnu-

If you're building TWRP with minimal manifest, append this command with the previous ones.

    export ALLOW_MISSING_DEPENDENCIES=true

Now, the build commands.  (bash is **mandatory**.)

    . build/envsetup.sh
    lunch omni_a50ub-eng
    make recoveryimage -j$(nproc --all)

After a successful build, the recovery and boot image are located at the following path.

    <recovery sources>/out/target/product/a50ub/

Compilation procedure is done, you can now flash this in your phone.