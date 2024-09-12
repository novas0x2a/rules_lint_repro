load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "aspect_rules_lint",
    sha256 = "fe2c8fc9419e5cd31ae63c1b8c3ae643b10a2befe810dcb8d142a7fe9554ec36",
    strip_prefix = "rules_lint-1.0.1",
    url = "https://github.com/aspect-build/rules_lint/releases/download/v1.0.1/rules_lint-v1.0.1.tar.gz",
)

# aspect_rules_lint depends on aspect_bazel_lib.
http_archive(
    name = "aspect_bazel_lib",
    sha256 = "6d758a8f646ecee7a3e294fbe4386daafbe0e5966723009c290d493f227c390b",
    strip_prefix = "bazel-lib-2.7.7",
    url = "https://github.com/aspect-build/bazel-lib/releases/download/v2.7.7/bazel-lib-v2.7.7.tar.gz",
)

load("@aspect_bazel_lib//lib:repositories.bzl", "aspect_bazel_lib_dependencies")

# aspect_bazel_lib depends on bazel_skylib
aspect_bazel_lib_dependencies()

load("@aspect_rules_lint//lint:ruff.bzl", "fetch_ruff")

# Specify a tag from the ruff repository
fetch_ruff("0.5.1")
