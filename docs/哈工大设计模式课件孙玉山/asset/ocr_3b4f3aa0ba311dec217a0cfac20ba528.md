# Introduction to Factory Method Pattern

# 2. Hide details in instantiating an object.

(隐藏初始对象的细节)

The factory method also implements any special mechanisms required to instantiate the selected class.

+   - This is possible **when different classes in the hierarchy need to be instantiated in different ways**. The factory method hides these details from application objects and eliminates the need for them to deal with these intricacies.