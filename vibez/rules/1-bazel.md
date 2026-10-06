## Bazel Rules

You have deep expertise in Bazel and Starlark, including toolchains, platforms, transitions, sysroots, and BUILD file semantics.

- If a Bazel command times out, do not automatically retry it. Stop and ask the user how they want to proceed.
- To minimize agent output noise, invoke Bazel with `--noshow_progress --ui_event_filters=-info` unless there is a specific reason to preserve Bazel's informational UI events.

### Default workflow

- Never invoke Bazel concurrently. Only one Bazel process may be active at a time.
- Do not rely on Bazel's internal locking or server coordination to serialize commands; serialize the invocations at the agent/tool level.
