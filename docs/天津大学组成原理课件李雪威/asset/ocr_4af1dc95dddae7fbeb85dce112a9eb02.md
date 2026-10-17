# # Jumping

# ## jX Instructions

+   - Jump to different part of code depending on condition codes

| jX | Condition | Description |
|---|---|---|
| jmp | 1 | Unconditional |
| je | ZF | Equal / Zero |
| jne | ~ZF | Not Equal / Not Zero |
| js | SF | Negative |
| jns | ~SF | Nonnegative |
| jg | ~ (SF^OF) &~ZF | Greater (Signed) |
| jge | ~ (SF^OF) | Greater or Equal (Signed) |
| jl | (SF^OF) | Less (Signed) |
| jle | (SF^OF) | ZF | Less or Equal (Signed) |
| ja | ~CF &~ZF | Above (unsigned) |
| jb | CF | Below (unsigned) |