# 1.5 Basic Program Execution Registers

# Segment Registers

The segment registers hold 16-bit segment selectors. A segment selector is a special pointer that identifies a segment in memory.

+   - CS - point to the code segment
+   - SS - point to the stack segment
+   - DS - point to the data segment
+   - ES - point to the data segment
+   - FS, GS - point to the data segment
+     - FS and GS not uses in 16 bits assembler

|  |
|---|---|
| Stack Segment |  |
| Data segment |  |
| Data segment |  |
| Code segment |  |
| ...... |  |