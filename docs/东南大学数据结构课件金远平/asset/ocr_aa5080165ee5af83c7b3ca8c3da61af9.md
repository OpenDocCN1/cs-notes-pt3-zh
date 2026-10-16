At the beginning, we can set front = rear = -1, and front == rear means that the queue is empty.

As we push and pop the queue, front may be > 0, and rear may be = capacity − 1.

In that case, we cannot add an element to the queue without shifting all elements to the left, as shown below:

![](bbox=[0.096, 0.6, 0.93, 0.86])