# Example 2: Module Decomposition View (Textual Outline)

**Behavior-Hiding Module**
- Function Driver Module
- Air Data Computer Module
- Audible Signal Module
- Computer Fail Signal Module
- Doppler Radar Module
- Flight Information Display Module
- Forward Looking Radar Module
- Head-Up Display Module
- Inertial Measurement Set Module
- Panel Module
- Radio Frequency Module
- Shared Services Module
- Mode Determination Module
- Panel I/O Support Module
- Safety-Bound Module
- Stage Detector Module
- System Value Module

**Software Decision Module**
- Application Data Type Module
- Numeric Data Types
- State Transition Event Mod.
- Data Bank Module
- Singleton Values Module
- Complex Event Module
- Filter Behavior Module
- Physical Models Module
- Aircraft Motion Module
- Earth Coordinate Module
- Target Behavior Module
- Weapons Behavior Module
- Software Utility Module
- Power-Up Initialization Module
- Numerical Algorithms Module
- System Generation Module
- System Generation Parameter Mod.
- Support Software Module

# Uses Style

+   - **Elements:** modules
+   - **Relations:** uses, a specialization of “depends on”
+     - A uses B if A depends on the presence of a correctly functioning B to satisfy its (A’s) own requirements.
+   - **Typology:** no constraints (However, loops can cause problems in incrementally system delivery.)
+   - **What it’s for:**
+     - Planning incremental development
+     - System extension
+     - Debugging and testing
+     - Gauging the effects of specific changes.

# Example 3: Module “Uses” View in UML

![](bbox=[0.159, 0.449, 0.395, 0.594])

# Example 4: Module “Uses” View (Table)

| Module Name | A | B | C | D | E |
|---|---|---|---|---|---|
| A |  | √ |  |  |  |
| B |  |  | √ |  |  |
| C |  |  |  |  |  |
| D |  |  |  |  |  |
| E |  |  |  |  |  |

√ = Module in row uses module in column

# Example 5: Module Generalization View in UML

![](bbox=[0.142, 0.703, 0.422, 0.854])

# Example 6: Module Layered View (Informal Notation)

![](bbox=[0.545, 0.713, 0.902, 0.871])