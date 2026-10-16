# Schedule Produced by Validation

+   Example of schedule produced using validation

| T₂₅ | T₂₆ |
|---|---|
| read (B) | |
|  | read (B) |
|  | B := B 50 |
|  | read (A) |
|  | A := A + 50 |
| read (A) | |
| ⟨ validate ⟩ | |
| display (A + B) | |
|  | ⟨ validate ⟩ |
|  | write (B) |
|  | write (A) |