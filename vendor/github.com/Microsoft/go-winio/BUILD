load("@io_bazel_rules_go//go:def.bzl", "go_library")

go_library(
    name = "go_default_library",
    srcs = [
        "backup.go",
        "ea.go",
        "file.go",
        "fileinfo.go",
        "hvsock.go",
        "pipe.go",
        "privilege.go",
        "reparse.go",
        "sd.go",
        "syscall.go",
        "zsyscall_windows.go",
    ],
    importmap = "k8s.io/kubernetes/vendor/github.com/Microsoft/go-winio",
    importpath = "github.com/Microsoft/go-winio",
    visibility = ["//visibility:public"],
    deps = [
        "//vendor/github.com/Microsoft/go-winio/pkg/guid:go_default_library",
    ] + select({
        "@io_bazel_rules_go//go/platform:windows": [
            "//vendor/golang.org/x/sys/windows:go_default_library",
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
        "//vendor/github.com/Microsoft/go-winio/pkg/guid:all-srcs",
        "//vendor/github.com/Microsoft/go-winio/vhd:all-srcs",
    ],
    tags = ["automanaged"],
    visibility = ["//visibility:public"],
)
