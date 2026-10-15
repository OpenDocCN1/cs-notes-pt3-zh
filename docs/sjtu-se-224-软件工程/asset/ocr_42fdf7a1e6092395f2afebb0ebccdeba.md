# Relationships: Dependency

+   - A relationship between two classes where a change in one may cause a change in the other
+   - Non-structural, "using" relationship

# Dependencies vs. Associations

+   - Associations are structural relationships
+   - Dependencies are non-structural relationships
+   - In order for objects to "know each other" they must be visible
+     - Local variable reference
+     - Parameter reference
+     - Global reference
+     - Field reference

# Local Variable Visibility

+   - The op1() operation contains a local variable of type ClassB

# Parameter Visibility

+   - The ClassB instance is passed to the ClassA instance

# Global Visibility

+   - The ClassUtility instance is visible because it is global

# Example: Conceptual Model