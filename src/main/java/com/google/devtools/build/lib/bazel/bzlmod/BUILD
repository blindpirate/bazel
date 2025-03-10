load("@rules_java//java:defs.bzl", "java_library")

package(
    default_visibility = ["//src:__subpackages__"],
)

licenses(["notice"])

filegroup(
    name = "srcs",
    srcs = glob(["*"]),
    visibility = ["//src:__subpackages__"],
)

java_library(
    name = "common",
    srcs = [
        "ArchiveRepoSpecBuilder.java",
        "ModuleKey.java",
        "RepoSpec.java",
        "Version.java",
    ],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/net/starlark/java/eval",
        "//third_party:auto_value",
        "//third_party:guava",
        "//third_party:jsr305",
    ],
)

java_library(
    name = "exception",
    srcs = ["ExternalDepsException.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/skyframe:detailed_exceptions",
        "//src/main/java/com/google/devtools/build/lib/util:detailed_exit_code",
        "//src/main/protobuf:failure_details_java_proto",
        "//third_party:error_prone_annotations",
        "//third_party:jsr305",
    ],
)

java_library(
    name = "module_extension",
    srcs = [
        "ModuleExtension.java",
        "ModuleExtensionId.java",
        "ModuleExtensionUsage.java",
        "Tag.java",
        "TagClass.java",
    ],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/net/starlark/java/annot",
        "//src/main/java/net/starlark/java/eval",
        "//src/main/java/net/starlark/java/syntax",
        "//third_party:auto_value",
        "//third_party:guava",
        "//third_party:jsr305",
    ],
)

java_library(
    name = "registry",
    srcs = [
        "IndexRegistry.java",
        "Registry.java",
        "RegistryFactory.java",
        "RegistryFactoryImpl.java",
    ],
    deps = [
        ":common",
        "//src/main/java/com/google/devtools/build/lib/bazel/repository/downloader",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//third_party:gson",
        "//third_party:guava",
    ],
)

java_library(
    name = "resolution",
    srcs = [
        "AbridgedModule.java",
        "ArchiveOverride.java",
        "BazelModuleResolutionValue.java",
        "GitOverride.java",
        "LocalPathOverride.java",
        "Module.java",
        "ModuleExtensionEvalStarlarkThreadContext.java",
        "ModuleExtensionResolutionValue.java",
        "ModuleFileValue.java",
        "ModuleOverride.java",
        "MultipleVersionOverride.java",
        "NonRegistryOverride.java",
        "RegistryOverride.java",
        "SingleExtensionEvalValue.java",
        "SingleExtensionUsagesValue.java",
        "SingleVersionOverride.java",
    ],
    deps = [
        ":common",
        ":module_extension",
        ":registry",
        ":repo_rule_creator",
        "//src/main/java/com/google/devtools/build/lib/analysis:blaze_directories",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/concurrent",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/skyframe:sky_functions",
        "//src/main/java/com/google/devtools/build/lib/skyframe/serialization/autocodec",
        "//src/main/java/com/google/devtools/build/lib/skyframe/serialization/autocodec:serialization-constant",
        "//src/main/java/com/google/devtools/build/skyframe:skyframe-objects",
        "//src/main/java/net/starlark/java/eval",
        "//src/main/java/net/starlark/java/syntax",
        "//third_party:auto_value",
        "//third_party:guava",
        "//third_party:jsr305",
    ],
)

java_library(
    name = "resolution_impl",
    srcs = [
        "BazelModuleResolutionFunction.java",
        "Discovery.java",
        "ModuleExtensionContext.java",
        "ModuleExtensionResolutionFunction.java",
        "ModuleFileFunction.java",
        "ModuleFileGlobals.java",
        "Selection.java",
        "SingleExtensionEvalFunction.java",
        "SingleExtensionUsagesFunction.java",
        "StarlarkBazelModule.java",
        "TypeCheckedTag.java",
    ],
    deps = [
        ":common",
        ":exception",
        ":module_extension",
        ":registry",
        ":resolution",
        "//src/main/java/com/google/devtools/build/docgen/annot",
        "//src/main/java/com/google/devtools/build/lib:runtime",
        "//src/main/java/com/google/devtools/build/lib/actions:file_metadata",
        "//src/main/java/com/google/devtools/build/lib/analysis:blaze_directories",
        "//src/main/java/com/google/devtools/build/lib/bazel/repository:repository_options",
        "//src/main/java/com/google/devtools/build/lib/bazel/repository/downloader",
        "//src/main/java/com/google/devtools/build/lib/bazel/repository/starlark",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/rules:repository/repository_directory_value",
        "//src/main/java/com/google/devtools/build/lib/rules:repository/repository_function",
        "//src/main/java/com/google/devtools/build/lib/skyframe:bzl_load_value",
        "//src/main/java/com/google/devtools/build/lib/skyframe:precomputed_value",
        "//src/main/java/com/google/devtools/build/lib/skyframe:skyframe_cluster",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/com/google/devtools/build/lib/vfs:pathfragment",
        "//src/main/java/com/google/devtools/build/skyframe",
        "//src/main/java/com/google/devtools/build/skyframe:skyframe-objects",
        "//src/main/java/net/starlark/java/annot",
        "//src/main/java/net/starlark/java/eval",
        "//src/main/java/net/starlark/java/syntax",
        "//src/main/protobuf:failure_details_java_proto",
        "//third_party:auto_value",
        "//third_party:guava",
        "//third_party:jsr305",
    ],
)

java_library(
    name = "repo_rule_value",
    srcs = [
        "BzlmodRepoRuleValue.java",
    ],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/concurrent",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/skyframe/serialization/autocodec",
        "//src/main/java/com/google/devtools/build/skyframe:skyframe-objects",
        "//third_party:guava",
    ],
)

java_library(
    name = "repo_rule_helper",
    srcs = [
        "BzlmodRepoRuleHelper.java",
        "BzlmodRepoRuleHelperImpl.java",
    ],
    deps = [
        ":common",
        ":registry",
        ":resolution",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/skyframe",
        "//third_party:guava",
        "//third_party:jsr305",
    ],
)

java_library(
    name = "repo_rule_creator",
    srcs = ["BzlmodRepoRuleCreator.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib/analysis:blaze_directories",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/events",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/main/java/com/google/devtools/build/lib/vfs",
        "//src/main/java/net/starlark/java/eval",
        "//src/main/java/net/starlark/java/syntax",
        "//third_party:guava",
    ],
)

java_library(
    name = "inspection",
    srcs = [
        "BazelModuleInspectorFunction.java",
        "BazelModuleInspectorValue.java",
        "ModqueryExecutor.java",
    ],
    deps = [
        ":common",
        ":resolution",
        "//src/main/java/com/google/devtools/build/lib/skyframe:sky_functions",
        "//src/main/java/com/google/devtools/build/lib/skyframe/serialization/autocodec:serialization-constant",
        "//src/main/java/com/google/devtools/build/lib/util/io",
        "//src/main/java/com/google/devtools/build/skyframe",
        "//src/main/java/com/google/devtools/build/skyframe:skyframe-objects",
        "//third_party:auto_value",
        "//third_party:guava",
        "//third_party:jsr305",
    ],
)
