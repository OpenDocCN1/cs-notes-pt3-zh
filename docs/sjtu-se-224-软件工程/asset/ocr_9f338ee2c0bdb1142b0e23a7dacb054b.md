# # Definitions: Transitions

+   - A transition is a relationship between **two states** that indicates that when an event occurs, the object moves from the prior state to the subsequent state

+   - ## Kinds of Transitions

| Transition Kind | Description | Syntax |
|---|---|---|
| entry transition | The specification of an **entry activity** that is executed when a state is entered | `entry/ activity` |
| exit transition | The specification of an **exit activity** that is executed when a state is exited | `exit/ activity` |
| external transition | A response to an event that causes a change of state or a self-transition, together with a specified effect. It may also cause the execution of exit and/or entry activities for states that are exited or entered. | `e(a:T)[guard]/activity` |
| internal transition | A response to an event that causes the execution of an effect but does not cause a change of state or execution of exit or entry activities | `e(a:T)[guard]/activity` |

![](bbox=[0.023, 0.469, 0.508, 0.612])