# Fuzzing TensorFlow.

load(
    "//tensorflow/core/platform:build_config.bzl",
    "tf_proto_library",
)
load(
    "//tensorflow/security/fuzzing:tf_fuzzing.bzl",
    "tf_cc_fuzz_test",
)

package(
    # copybara:uncomment default_applicable_licenses = ["//tensorflow:license"],
    licenses = ["notice"],
)

tf_cc_fuzz_test(
    name = "stringprintf_fuzz",
    srcs = ["stringprintf_fuzz.cc"],
    tags = ["no_oss"],
    deps = [
        "//tensorflow/core/platform:stringprintf",
    ],
)

cc_library(
    name = "fuzz_session",
    testonly = 1,
    hdrs = ["fuzz_session.h"],
    tags = ["no_oss"],
    visibility = [
        "//tensorflow/cc/framework/fuzzing:__subpackages__",
        "//tensorflow/security/fuzzing:__subpackages__",
    ],
    deps = [
        "//tensorflow/cc:scope",
        "//tensorflow/core:core_cpu_base",
        "//tensorflow/core:session_options",
        "//tensorflow/core/common_runtime:direct_session_internal",
        "//tensorflow/core/framework:tensor",
        "//tensorflow/core/platform:status",
        "@com_google_fuzztest//fuzztest",
    ],
)

