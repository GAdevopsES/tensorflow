load("//tensorflow:tensorflow.bzl", "tf_cc_test")
load("//tensorflow:tensorflow.bzl", "get_compatible_with_portable")
load("//tensorflow/core/platform:build_config.bzl", "tf_platform_deps")
load("//tensorflow/core/platform:rules_cc.bzl", "cc_library")

package(
    default_visibility = [
        "//tensorflow:internal",
        "@tf_runtime//:friends",
    ],
    licenses = ["notice"],
)

cc_library(
    name = "arguments",
    srcs = ["arguments.cc"],
    hdrs = ["arguments.h"],
    compatible_with = get_compatible_with_portable(),
    deps = [
        ":types",
        "//tensorflow/compiler/xla/mlir/transforms/runtime:type_converter",
        "@llvm-project//llvm:Support",
        "@tf_runtime//:dtype",
        "@tf_runtime//:support",
    ],
)

tf_cc_test(
    name = "arguments_test",
    srcs = ["arguments_test.cc"],
    deps = [
        ":arguments",
        ":types",
        "//tensorflow/core:test",
        "//tensorflow/core:test_main",
        "@llvm-project//llvm:Support",
        "@tf_runtime//:dtype",
    ],
)

cc_library(
    name = "async_runtime",
    srcs = ["async_runtime.cc"],
    hdrs = ["async_runtime.h"],
    compatible_with = get_compatible_with_portable(),
    deps = [
        "//tensorflow/core/platform:mutex",
        "//tensorflow/core/platform:types",
        "//third_party/eigen3",
        "@llvm-project//llvm:Support",
        "@tf_runtime//:hostcontext",
        "@tf_runtime//:support",
    ],
)

cc_library(
    name = "async_values_cache",
    hdrs = ["async_values_cache.h"],
    compatible_with = get_compatible_with_portable(),
    deps = [
        "//tensorflow/core/platform:platform",
    ] + tf_platform_deps(
        "async_values_cache",
        platform_dir = "//tensorflow/compiler/xla/runtime/",
    ),
)

cc_library(
    name = "constraints",
    srcs = ["constraints.cc"],
    hdrs = ["constraints.h"],
    compatible_with = get_compatible_with_portable(),
    deps = [
        "@llvm-project//llvm:Support",
        "@tf_runtime//:support",
    ],
)

cc_library(
    name = "diagnostics",
    srcs = ["diagnostics.cc"],
    hdrs = ["diagnostics.h"],
    compatible_with = get_compatible_with_portable(),
    deps = [
        ":logical_result",
        "@llvm-project//llvm:Support",
    ],
)

tf_cc_test(
    name = "diagnostics_test",
    srcs = ["diagnostics_test.cc"],
    deps = [
        ":diagnostics",
        "//tensorflow/core:test",
        "//tensorflow/core:test_main",
        "@llvm-project//llvm:Support",
        "@tf_runtime//:dtype",
        "@tf_runtime//:support",
    ],
)

cc_library(
    name = "logical_result",
    hdrs = ["logical_result.h"],
    compatible_with = get_compatible_with_portable(),
    deps = ["@llvm-project//mlir:Support"],
)

cc_library(
    name = "memory_mapper",
    srcs = ["memory_mapper.cc"],
    hdrs = ["memory_mapper.h"],
    compatible_with = get_compatible_with_portable(),
    deps = [
        "//tensorflow/core/platform:platform",
        "@llvm-project//llvm:ExecutionEngine",
        "@llvm-project//llvm:Support",
    ] + tf_platform_deps(
        "memory_mapper",
        platform_dir = "//tensorflow/compiler/xla/runtime/",
    ),
)

cc_library(
    name = "runtime",
    hdrs = ["runtime.h"],
    compatible_with = get_compatible_with_portable(),
)

cc_library(
    name = "symbolic_shape",
    srcs = ["symbolic_shape.cc"],
    hdrs = ["symbolic_shape.h"],
    compatible_with = get_compatible_with_portable(),
    deps = [
        ":arguments",
        ":constraints",
        ":types",
        "@llvm-project//llvm:Support",
        "@tf_runtime//:support",
    ],
)

tf_cc_test(
    name = "symbolic_shape_test",
    srcs = ["symbolic_shape_test.cc"],
    deps = [
        ":arguments",
        ":constraints",
        ":symbolic_shape",
        ":types",
        "//tensorflow/core:test",
        "//tensorflow/core:test_main",
        "@llvm-project//llvm:Support",
        "@tf_runtime//:dtype",
    ],
)

cc_library(
    name = "types",
    srcs = ["types.cc"],
    hdrs = ["types.h"],
    compatible_with = get_compatible_with_portable(),
    deps = [
        "@llvm-project//llvm:Support",
        "@tf_runtime//:dtype",
        "@tf_runtime//:support",
    ],
)

cc_library(
    name = "type_id",
    hdrs = ["type_id.h"],
    compatible_with = get_compatible_with_portable(),
    deps = ["@llvm-project//mlir:Support"],
)
