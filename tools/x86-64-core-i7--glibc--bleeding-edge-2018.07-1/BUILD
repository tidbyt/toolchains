package(default_visibility = ["//visibility:public"])

load(":cc_toolchain_config.bzl", "cc_toolchain_config")

cc_toolchain_config(
    name = "x86_64_toolchain_config",
    cpu = "x86_64",
)

cc_toolchain_suite(
    name = "toolchain",
    # target_cpu | compiler
    toolchains = {
        "x86_64|gcc": "bootlin-x86_64",
        "x86_64": "bootlin-x86_64",
    },
)

filegroup(
    name = "linux_all_files",
    srcs = [
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:tool-wrappers",
        "@bootlin_x86_64_toolchain//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_linker_files",
    srcs = [
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:ar",
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:gcc",
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:ld",
        "@bootlin_x86_64_toolchain//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_compiler_files",
    srcs = [
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:as",
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:gcc",
        "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:ld",
        "@bootlin_x86_64_toolchain//:compiler_pieces",
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
    name = "bootlin-x86_64",
    all_files = ":linux_all_files",
    ar_files = "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:ar",
    as_files = "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:as",
    compiler_files = ":linux_compiler_files",
    dwp_files = ":empty",
    dynamic_runtime_lib = ":empty",
    linker_files = ":linux_linker_files",
    objcopy_files = "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:objcopy",
    static_runtime_lib = ":empty",
    strip_files = "//tools/x86-64-core-i7--glibc--bleeding-edge-2018.07-1/x86_64-linux:strip",
    supports_param_files = 1,
    toolchain_config = ":x86_64_toolchain_config",
    toolchain_identifier = "x86_64_toolchain",
    visibility = ["//visibility:public"],
)
