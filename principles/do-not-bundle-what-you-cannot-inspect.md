# Do Not Bundle What You Cannot Inspect

Source handoffs should make included files, dependency content, generated metadata, and consumption configuration visible before another project, tool, reviewer, or AI agent consumes them.

This principle applies to local source snapshots, dependency handoffs, packaging outputs, extraction workflows, and language-native source transfer mechanisms.

Expected properties:

- the source handoff can be inspected before consumption
- included files or dependency content can be enumerated
- generated metadata explains how the consumer will use the handoff
- changes to the handoff process are version-controlled

This does not mean bundled source is automatically safe. It means the receiver can see what is being handed over before relying on it.
