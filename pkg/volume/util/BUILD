load("@io_bazel_rules_go//go:def.bzl", "go_library", "go_test")

go_library(
    name = "go_default_library",
    srcs = [
        "atomic_writer.go",
        "attach_limit.go",
        "device_util.go",
        "device_util_linux.go",
        "device_util_unsupported.go",
        "doc.go",
        "finalizer.go",
        "io_util.go",
        "metrics.go",
        "nested_volumes.go",
        "resize_util.go",
        "util.go",
    ],
    importpath = "k8s.io/kubernetes/pkg/volume/util",
    visibility = ["//visibility:public"],
    deps = [
        "//pkg/api/legacyscheme:go_default_library",
        "//pkg/apis/core/v1/helper:go_default_library",
        "//pkg/features:go_default_library",
        "//pkg/util/mount:go_default_library",
        "//pkg/util/resizefs:go_default_library",
        "//pkg/volume:go_default_library",
        "//pkg/volume/util/types:go_default_library",
        "//pkg/volume/util/volumepathhandler:go_default_library",
        "//staging/src/k8s.io/api/core/v1:go_default_library",
        "//staging/src/k8s.io/api/storage/v1:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/api/meta:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/api/resource:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/apis/meta/v1:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/apis/meta/v1/unstructured:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/labels:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/runtime:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/types:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/util/sets:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/util/strategicpatch:go_default_library",
        "//staging/src/k8s.io/apiserver/pkg/util/feature:go_default_library",
        "//staging/src/k8s.io/client-go/kubernetes:go_default_library",
        "//vendor/github.com/prometheus/client_golang/prometheus:go_default_library",
        "//vendor/k8s.io/klog:go_default_library",
        "//vendor/k8s.io/utils/strings:go_default_library",
    ],
)

go_test(
    name = "go_default_test",
    srcs = [
        "atomic_writer_test.go",
        "attach_limit_test.go",
        "device_util_linux_test.go",
        "nested_volumes_test.go",
        "resize_util_test.go",
        "util_test.go",
    ],
    embed = [":go_default_library"],
    deps = [
        "//pkg/apis/core/install:go_default_library",
        "//pkg/apis/core/v1/helper:go_default_library",
        "//pkg/util/slice:go_default_library",
        "//pkg/volume:go_default_library",
        "//staging/src/k8s.io/api/core/v1:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/api/resource:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/apis/meta/v1:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/types:go_default_library",
        "//staging/src/k8s.io/apimachinery/pkg/util/sets:go_default_library",
    ] + select({
        "@io_bazel_rules_go//go/platform:linux": [
            "//staging/src/k8s.io/client-go/util/testing:go_default_library",
        ],
        "//conditions:default": [],
    }),
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [
        ":package-srcs",
        "//pkg/volume/util/exec:all-srcs",
        "//pkg/volume/util/fs:all-srcs",
        "//pkg/volume/util/nestedpendingoperations:all-srcs",
        "//pkg/volume/util/nsenter:all-srcs",
        "//pkg/volume/util/operationexecutor:all-srcs",
        "//pkg/volume/util/recyclerclient:all-srcs",
        "//pkg/volume/util/subpath:all-srcs",
        "//pkg/volume/util/types:all-srcs",
        "//pkg/volume/util/volumepathhandler:all-srcs",
    ],
    tags = ["automanaged"],
    visibility = ["//visibility:public"],
)
