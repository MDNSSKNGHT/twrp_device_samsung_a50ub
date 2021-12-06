# Recovery Device Tree for SM-A505G (Galaxy A50)

## How to compile
For compiling, you'll only need this repository.

If you're building TWRP with minimal manifest, execute this command.

    export ALLOW_MISSING_DEPENDENCIES=true

Now, the build commands.  (bash is **mandatory**.)

    . build/envsetup.sh
    lunch omni_a50ub-eng
    make recoveryimage -j$(nproc --all)

After a successful build, the recovery and boot image are located at the following path.

    <recovery sources>/out/target/product/a50ub/

Compilation procedure is done, you can now flash this in your phone.