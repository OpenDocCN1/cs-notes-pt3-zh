# The State Design Pattern

# 协作关系 (Collaborations)

+   a) **Context代表状态相关的请求。** Context delegates state-specific requests to the current ConcreteState object.

+   b) **Context可以将自己作为一个对象通过参数传递给状态子类对象，从而可以让状态对象访问Context类的方法。** A context may pass itself as an argument to the State object handling the request. This lets the State object access the context if necessary.