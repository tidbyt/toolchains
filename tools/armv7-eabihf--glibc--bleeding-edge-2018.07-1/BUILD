package(default_visibility = ["//visibility:public"])

load(":cc_toolchain_config.bzl", "cc_toolchain_config")

cc_toolchain_config(
    name = "armeabi-v7a_toolchain_config",
    cpu = "armeabi-v7a",
)

cc_toolchain_suite(
    name = "toolchain",
    # target_cpu | compiler
    toolchains = {
        "armeabi-v7a|gcc": "bootlin-armeabi-v7a",
        "armeabi-v7a": "bootlin-armeabi-v7a",
    },
)

filegroup(
    name = "linux_all_files",
    srcs = [
        "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:tool-wrappers",
        "@bootlin_arm_toolchain//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_linker_files",
    srcs = [
        "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:ar",
        "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:gcc",
        "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:ld",
        "@bootlin_arm_toolchain//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_compiler_files",
    srcs = [
        "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:as",
        "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:gcc",
        "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:ld",
        "@bootlin_arm_toolchain//:compiler_pieces",
    ],
)

# Here we'll keep things simple by including all files ditributed in archives.
filegroup(
    name = "all",
    srcs = glob(["**/*"]),
)

filegroup(
    name = "empty",
    srcs = [],
)

cc_toolchain(
    name = "bootlin-armeabi-v7a",
    all_files = ":linux_all_files",
    ar_files = "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:ar",
    as_files = "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:as",
    compiler_files = ":linux_compiler_files",
    dwp_files = ":empty",
    dynamic_runtime_lib = ":empty",
    linker_files = ":linux_linker_files",
    objcopy_files = "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:objcopy",
    static_runtime_lib = ":empty",
    strip_files = "//tools/armv7-eabihf--glibc--bleeding-edge-2018.07-1/arm-linux:strip",
    supports_param_files = 1,
    toolchain_config = ":armeabi-v7a_toolchain_config",
    toolchain_identifier = "armeabi-v7a_toolchain",
    visibility = ["//visibility:public"],
)
