load("@rules_java//java:defs.bzl", "java_binary", "java_library", "java_proto_library")
load("@rules_proto//proto:defs.bzl", "proto_library")

java_binary(
    name = "bazel-diff",
    main_class = "com.bazel_diff.BazelDiff",
    runtime_deps = [":java-bazel-diff-lib"],
    visibility = ["//visibility:public"]
)

java_library(
    name = "java-bazel-diff-lib",
    srcs = glob(["*.java"]),
    deps = [
        ":build_java_proto",
        "@com_google_protobuf//:protobuf_java",
        "@bazel_diff_maven//:info_picocli_picocli",
        "@bazel_diff_maven//:com_google_code_gson_gson",
        "@bazel_diff_maven//:com_google_guava_guava"
    ],
    visibility = ["//test/java/com/bazel_diff:__pkg__"]
)

java_proto_library(
    name = "build_java_proto",
    deps = [":build_proto"],
)

proto_library(
    name = "build_proto",
    srcs = [":build_proto_gen"]
)

genrule(
    name = "build_proto_gen",
    srcs = ["@bazel_tools//src/main/protobuf:build.proto"],
    outs = ["build.proto"],
    cmd = "cp $< $@"
)
