load("@build_bazel_rules_apple//apple:ios.bzl", "ios_application")
load("@build_bazel_rules_apple//apple:versioning.bzl", "apple_bundle_version")
load("@rules_xcodeproj//xcodeproj:defs.bzl", "top_level_target", "xcodeproj")

package(default_visibility = ["//visibility:public"])

licenses(["notice"])

objc_library(
    name = "Sources",
    srcs = [
        "Sources/AppDelegate.h",
        "Sources/AppDelegate.m",
        "Sources/main.m",
    ],
    data = [
        "Resources/Main.storyboard",
    ],
    tags = ["manual"],
    deps = [
        "//vendor:libhello",
    ],
)

apple_bundle_version(
    name = "ios_demo_version",
    build_version = "1.0",
)

ios_application(
    name = "ios_demo",
    bundle_id = "live.bilibili.com",
    entitlements = "//profiles:live_development.entitlements",
    provisioning_profile = "//profiles:live_development.mobileprovision",
    families = [
        "iphone",
        "ipad",
    ],
    infoplists = [":Info.plist"],
    minimum_os_version = "11.0",
    version = ":ios_demo_version",
    deps = [":Sources"],
)

xcodeproj(
    name = "xcodeproj",
    project_name = "ios_demo",
    tags = ["manual"],
    top_level_targets = [
        top_level_target(":ios_demo", target_environments = ["device", "simulator"]),
    ],
)


