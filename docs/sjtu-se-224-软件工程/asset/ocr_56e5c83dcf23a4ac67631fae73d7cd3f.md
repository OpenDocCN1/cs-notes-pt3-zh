# Kinds of States

| State Kind | Description | Notation |
|---|---|---|
| submachine state | A state that references a state machine definition, which conceptually replaces the submachine state | s: M |
| entry point | A externally visible pseudostate within a state machine that identifies an internal state as a target | a → ○ T |
| exit point | A externally visible pseudostate within a state machine that identifies an internal state as a source | U ○× b → |