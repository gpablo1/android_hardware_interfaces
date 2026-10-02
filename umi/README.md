# UMI legacy HIDL interfaces

Fork: gpablo1/android_hardware_interfaces, umi-calcite.
Base AOSPA revision: c0fa2c83463785fd25d6e6813934b7a3ed4dfa44.
Pinned source revision: b738b163e417c4a162f1b3557037073a328a916b.

FCM level 6 references HIDL interfaces removed upstream. This fork restores only original interface definitions and frozen hashes: IR 1.0, dumpstate 1.0/1.1, input common/classifier 1.0 and surround view 1.0. It does not install example services or alter the matrix.

Sources are the parents of AOSPA removals d8241bb3e7ad6eaa02a5958f8c9e03e99aa98595, 97e6692fa81fd6a5e610e91cd85fc8ff7ac54b19, 5ab06c939659d299d41b253ff0df006b00c7bf16 and d5411978da2bb9ad0d8d71cb148c601c45c85d0b.

## Restore on another server

Initialize the same Calcite and UMI manifests. Save this branch umi/manifest.xml as .repo/local_manifests/zz-umi-interfaces.xml before synchronizing. The base manifest must already declare AOSPA/android_hardware_interfaces. This override replaces only that project and fixes the source SHA; it does not pin the rest of the ROM. Keep the separate UMI audio override. Check the effective manifest has exactly one hardware/interfaces entry owned by gpablo1 at the pinned SHA.

## Permissions

AGENTS.md must permit hardware/interfaces only as the personal fork gpablo1/android_hardware_interfaces and permit only this manifest override. Keep upstream and all other shared hardware repositories read-only.

## Validation

All six restored packages pass hidl-gen -Lhash; their 13 hashes match the original published API records. git apply --check passed before integration. Targeted `m check-vintf-all -j8` passed on the UMI Calcite workspace (return code 0, 09:14), reporting COMPATIBLE. Local log: /tmp/umi_interfaces_vintf_validation.log. Full ROM and device runtime validation are separate. Exact source revisions and filenames are recorded in umi/provenance.json.
