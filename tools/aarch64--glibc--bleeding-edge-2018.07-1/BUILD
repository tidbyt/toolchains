package(default_visibility = ["//visibility:public"])

load(":cc_toolchain_config.bzl", "cc_toolchain_config")

cc_toolchain_config(
    name = "aarch64_toolchain_config",
    cpu = "aarch64",
)

cc_toolchain_suite(
    name = "toolchain",
    # target_cpu | compiler
    toolchains = {
        "aarch64|gcc": "bootlin-aarch64",
        "aarch64": "bootlin-aarch64",
    },
)

filegroup(
    name = "linux_all_files",
    srcs = [
        "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:tool-wrappers",
        "@bootlin_aarch64_toolchain//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_linker_files",
    srcs = [
        "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:ar",
        "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:gcc",
        "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:ld",
        "@bootlin_aarch64_toolchain//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_compiler_files",
    srcs = [
        "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:as",
        "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:gcc",
        "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:ld",
        "@bootlin_aarch64_toolchain//:compiler_pieces",
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
    name = "bootlin-aarch64",
    all_files = ":linux_all_files",
    ar_files = "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:ar",
    as_files = "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:as",
    compiler_files = ":linux_compiler_files",
    dwp_files = ":empty",
    dynamic_runtime_lib = ":empty",
    linker_files = ":linux_linker_files",
    objcopy_files = "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:objcopy",
    static_runtime_lib = ":empty",
    strip_files = "//tools/aarch64--glibc--bleeding-edge-2018.07-1/aarch64-linux:strip",
    supports_param_files = 1,
    toolchain_config = ":aarch64_toolchain_config",
    toolchain_identifier = "aarch64_toolchain",
    visibility = ["//visibility:public"],
)
