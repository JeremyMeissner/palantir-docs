---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arrayJoinV1/"
title: "Join array"
---
# Join array

Supported in: Batch, Faster, Streaming. Joins array with specified separator. Expression categories: Array. Declared arguments. Array to join: Array to join on. Expression<Array<String>> Separator: Separator to join array with. Expression<String> Output type: String. Examples. Example 1: Base case. Argument values: Array to join: [ hello, world ] Separator: - Output: hello-world. Example 2: Base case. Argument values: Array to join: [ hello, world ] Separator: Output: hello world. Example 3: Null case. Argument values: Array to join: array. Separator: separator. arrayseparatorOutput [ hello, world ] null. helloworld. null. - null. null. null. null. Example 4: Edge case. Argument values: Array to join: [ ] Separator: - Output: empty string.
