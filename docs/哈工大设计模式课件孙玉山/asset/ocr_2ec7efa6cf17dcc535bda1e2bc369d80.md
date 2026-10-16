# Introduction to the strategy pattern through Design of a sorting program

The source code may look like the following

```
Public class Client {
    public static void main(String[] args){
        Sorting s = new Sorting();
        int[] nums={7, 9, 2, 45, 21, 87, 66, 32};

        if ( args[0] == 1 )
            s.bubbleSort(nums); //调用Sorting中的方法

        else if ( args[0] == 2 )
            s.heapSort(nums);

        ...
    }
}
```