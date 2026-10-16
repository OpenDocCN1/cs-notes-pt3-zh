
## Example of design using strategy pattern

```
class ButtonListener implements ActionListener {
    public void actionPerformed(ActionEvent ae) {
        if (ae.getActionCommand().equals(SORT)) {
            if (type.equals(BUBBLE))
                sa = new BubbleSort();
            if (type.equals(HEAP))
                sa = new HeapSort();
            if (type.equals(INSERT))
                sa = new InsertSort();
            if (type.equals(QUICK))
                sa = new QuickSort();

            context = new Context(sa);
            intArray = context.sortIntArray(intArray);
            long eTime = context.getExeTime();
        }
    }
}
```

- 1. 用户创建策略子类对象 sa
- 2. 将sa作为创建Context类的对象的参数传递给 Context
- 3. 在用户类中使用Context对象调用 sortIntArray(intArray) getExeTime()方法

## Example of design using strategy pattern

```
class Context {
  SortAlgorithm alg;
  private long startTime;
  private long endTime;

  public Context(SortAlgorithm alg) {
    this.alg = alg;
  }
  public int[] sortIntArray(int[] a) {
    return this.alg.sort(a, this);
  }
  public void startExecution(){
    startTime = System.currentTimeMillis();
  }
  public void endExecution(){
    endTime = System.currentTimeMillis();
  }
  public long getExeTime(){
    long exeTime=0;
    exeTime = endTime-startTime;
    return exeTime;
  }
}
```

- 1. 策略子类对象alg由构造函数传入
- 2. 在sortIntArray方法中，直接使用alg调用策略类的sort方法
- 3. 同时，将Context对象传递给策略类
- 4. 策略类利用该Context对象调用计算程序执行时间的方法 startExecution() endExecution()

## Example of design using strategy pattern

```
public interface SortAlgorithm {
    int[] sort(int[] nums, Context ct);
}
```

## Example of design using strategy pattern

```
public class BubbleSort implements SortAlgorithm {
    public int[] sort(int[] intArray, Context ct){
        ct.startExecution();
        for(int i = intArray.length; --i >= 0;)
            for(int j = 0; j < i; j++){
                if(intArray[j] > intArray[j + 1]){
                    int T = intArray[j];
                    intArray[j] = intArray[j + 1];
                    intArray[j + 1] = T;
                }
            }
        ct.endExecution();
        return intArray;
    }
}
```

## Example of design using strategy pattern

```
public class InsertSort implements SortAlgorithm {
    public int[] sort(int[] intArray, Context ct){
        ct.startExecution();
        for (int i = 1; i < intArray.length; i++){
            int j = i;
            int numToBeInserted = intArray[i];
            while ((j > 0) && (intArray[j-1] > numToBeInserted)) {
                intArray[j] = intArray[j-1];
                j--;
            }
            intArray[j] = numToBeInserted;
        }
        ct.endExecution();
        return intArray;
    }
}
```

## Example of design using strategy pattern

【例3】十二属相(Chinese Zodiac)介绍: 我们要设计一个介绍中国十二属相的程序。我们试图使用策略模式对以上问题进行设计。

- - 首先，我们将十二属相各自封装为一个类。并且为这些类设计一个共同的接口ChineseZodiac。
- - 用户使用用户图形界面输入自己的出生年月日，并且在创建Context对象的时候，将日期作为参数传递给Context类。
- - Context类根据用户输入进行计算，得出应该初始的属相类，并且负责创建该属相类对象。Context类使用该对象调用子类的say()功能，介绍该属性的特点。
- - 设计类图如下。

## Example of design using strategy pattern

ClientGUI

-zodiac:ChineseZodiac
+Context(y:String,m:String, d: String)
+parseZodiac()
+setupZodiacToYear()
+createZodiacObj()
+getZodiacDescription()

<<interface>>
ChineseZodiac
+say()

zodiac

Rat
+say()

Ox
+say()

Tiger
+say()

Rabbit
+say()

利用策略模式设计的十二生肖特点介绍类图(有省略)

## Example of design using strategy pattern

ClientGUI

Context con = new Context(y,m,d);
con. getZodiacDescription()

# Context

-zodiac:ChineseZodiac

+Context(y, m, d)
+parseZodiac()
+setupZodiacToYear()
+createZodiacObj()
+getZodiacDescription()

zodiac

创建Tiger对象tg

# <<interface>>
ChineseZodiac

+say()

tg.say()

# Rat

+say()

# Ox

+say()

# Tiger

+say()

# Rabbit

+say()

## Example of design using strategy pattern

```
class ButtonListener implements ActionListener {
    public void actionPerformed(ActionEvent ae) {
        if (ae.getActionCommand().equals(FIND)) {
            String yr = getYear();
            String mon = getMonth();
            String date = getDate();
            Context context = new Context(yr, mon, date);
            String saying = context.getZodiacDescription();
            ImageIcon icon = context.getImageIcon();
            setImageInfo(icon);
            txtDisplayZodiac.setText("");
            showZodiacInfo(saying);
        }
    }
}
```

这里没有将具体的策略子类的对象传递给Context类
