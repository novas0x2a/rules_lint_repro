load("@aspect_bazel_lib//lib:transitions.bzl", "platform_transition_binary")

platform(
    name = "linux_x64",
    constraint_values = [
        "@platforms//os:linux",
        "@platforms//cpu:x86_64",
    ],
)

platform(
    name = "linux_arm64",
    constraint_values = [
        "@platforms//os:linux",
        "@platforms//cpu:aarch64",
    ],
)

alias(
    name = "v0",
    actual = select({
        "@bazel_tools//src/conditions:linux_x86_64": "@ruff_x86_64-unknown-linux-gnu//:ruff",
        "@bazel_tools//src/conditions:linux_aarch64": "@ruff_aarch64-unknown-linux-gnu//:ruff",
        "@bazel_tools//src/conditions:darwin_arm64": "@ruff_aarch64-apple-darwin//:ruff",
        "@bazel_tools//src/conditions:darwin_x86_64": "@ruff_x86_64-apple-darwin//:ruff",
        "@bazel_tools//src/conditions:windows_x64": "@ruff_x86_64-pc-windows-msvc//:ruff.exe",
    }),
)

# Workaround 1
platform_transition_binary(
    name = "v1",
    binary = ":v0",
    target_platform = "@local_config_platform//:host",
)

# Workaround 2

config_setting(
    name = "darwin_arm64_host",
    values = {"host_cpu": "darwin_arm64"},
)

config_setting(
    name = "darwin_x86_host",
    values = {"host_cpu": "darwin_x86_64"},
)

config_setting(
    name = "windows_x64_host",
    values = {"host_cpu": "x64_windows"},
)

config_setting(
    name = "linux_x86_host",
    values = {"host_cpu": "k8"},
)

config_setting(
    name = "linux_arm64_host",
    values = {"host_cpu": "aarch64"},
)

alias(
    name = "v2",
    actual = select({
        ":windows_x64_host": "@ruff_x86_64-pc-windows-msvc//:ruff.exe",
        ":darwin_x86_host": "@ruff_x86_64-apple-darwin//:ruff",
        ":darwin_arm64_host": "@ruff_aarch64-apple-darwin//:ruff",
        ":linux_x86_host": "@ruff_x86_64-unknown-linux-gnu//:ruff",
        ":linux_arm64_host": "@ruff_aarch64-unknown-linux-gnu//:ruff",
    }),
)
