
## Looping Control Structures

- Three different commands
  - while statement
  - do-while statement
  - ......

## The Do-While Statement

### Syntax

```cpp
do
  code block
while (bool expr);
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_379_0.png)

## Using a do while loop

```cpp
char reply;

do {
    ..........        // some code
    ..........
    cout << "Do you want to continue?(y):";
    cin >> reply;
} while(reply == 'y');
```

## Why use a ........?

- What is the advantage of a
- while:
- do...while:

## Looping Control Structures

- Three different commands
  - while statement
  - do-while statement
  - for statement

## 1. 多模态大语言模型(MLLM)

多模态大语言模型 (Multimodal Large Language Model， MLLM) 是指能够处理和融合多种模态信息 (如文本、图像、音频、视频等) 的大语言模型。

多模态大语言模型架构由模态编码器、输入投影器、大语言模型(LLM)和输出投影器组成。

## The for loop

- Syntax
  
  `for (initialization ; bool expression ; update action)`
  
  body of the loop

- Example
  
  ```cpp
  for (int i = 0; i < 3; i++) {
      cout << "i is " << i << endl;
  }
  ```

## Initialization

Executed once at the beginning of the for loop's execution

## Bool Exp

The Bool Exp is evaluated at the start of each iteration of the loop

true

false

## Body

## Update Action

## Execution Example

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_388_0.png)

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_389_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_391_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

i is 0

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_393_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_394_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_395_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_396_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_397_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

```
i is 0
i is 1
i is 2
```

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
    cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_399_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
cout << "i is " << i << endl;
}
cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_400_0.png)

## Execution Example

```cpp
for (int i = 0; i < 3; ++i) {
cout << "i is " << i << endl;
}

cout << "all done" << endl;
```

![](img/844f1d9b9fc3acdef1abfe5a062e4e8f_401_0.png)

## Embedding for loops

- Just like **while** loops, **for** loops can also be embedded inside other loops
- in fact, due to there compactness (information being easier to read) many embedded loops will be **for** loops
