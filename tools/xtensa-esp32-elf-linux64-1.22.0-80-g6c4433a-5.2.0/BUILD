package(default_visibility = ["//visibility:public"])

load(":cc_toolchain_config.bzl", "cc_toolchain_config")

cc_toolchain_config(
    name = "xtensa_toolchain_config",
    cpu = "xtensa",
)

cc_toolchain_suite(
    name = "toolchain",
    # target_cpu | compiler
    toolchains = {
        "xtensa|gcc": "bootlin-xtensa",
        "xtensa": "bootlin-xtensa",
    },
)

filegroup(
    name = "linux_all_files",
    srcs = [
        "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:tool-wrappers",
        "@xtensa_esp32_elf_linux64//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_linker_files",
    srcs = [
        "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:ar",
        "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:gcc",
        "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:ld",
        "@xtensa_esp32_elf_linux64//:compiler_pieces",
    ],
)

filegroup(
    name = "linux_compiler_files",
    srcs = [
        "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:as",
        "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:gcc",
        "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:ld",
        "@xtensa_esp32_elf_linux64//:compiler_pieces",
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
    name = "bootlin-xtensa",
    all_files = ":linux_all_files",
    ar_files = "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:ar",
    as_files = "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:as",
    compiler_files = ":linux_compiler_files",
    dwp_files = ":empty",
    dynamic_runtime_lib = ":empty",
    linker_files = ":linux_linker_files",
    objcopy_files = "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:objcopy",
    static_runtime_lib = ":empty",
    strip_files = "//tools/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0/xtensa-esp32-elf:strip",
    supports_param_files = 1,
    toolchain_config = ":xtensa_toolchain_config",
    toolchain_identifier = "xtensa_toolchain",
    visibility = ["//visibility:public"],
)
