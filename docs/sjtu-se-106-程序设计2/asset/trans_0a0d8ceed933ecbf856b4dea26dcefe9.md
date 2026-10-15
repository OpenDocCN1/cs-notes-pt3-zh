

## exp.h 接口

```
/*
 * Class: Expression
 * -----------------
 * This class is used to represent a node in an expression tree.
 * Expression is an example of an abstract class, which defines the
 * structure and behavior of a set of classes but has no objects of its
 * own.  Any object must be one of its three concrete subclasses:
 *
 * 1. ConstantExp   -- an integer constant
 * 2. IdentifierExp -- a string representing an identifier
 * 3. CompoundExp   -- two expressions combined by an operator
 *
 * The abstract class defines an interface common to all Expression objects;
 * each subclass provides its own implementation of the common interface.
 */

class Expression {
public:
    Expression();
    virtual ~Expression();
    virtual int eval(EvalState & state) = 0;
    virtual std::string toString() = 0;
    virtual ExpressionType type() = 0;
};
```

只能被重写的函数用 = 0 这样标记。

在 C++ 中，任何可以被其子类重写的方法都必须标记为 virtual。

## exp.h 接口

```
/*
 * Class: ConstantExp
 * ----------------
 * This subclass represents a constant integer expression.
 */

class ConstantExp: public Expression {
public:
    ConstantExp(int val);

    virtual int eval(EvalState & state);
    virtual std::string toString();
    virtual ExpressionType type();

    int getValue();

private:
    int value;
};
```

## exp.h 接口

```
/*
 * Class: IdentifierExp
 * ---------------------
 * This subclass represents a expression corresponding to a variable.
 */

class IdentifierExp: public Expression {
public:
    IdentifierExp(string name);
    virtual int eval(EvalState & state);
    virtual std::string toString();
    virtual ExpressionType type();
    string getName();

private:
    std::string name;
};
```

## `exp.h` 接口

```cpp
/*
 * Class: CompoundExp
 * -------------------
 * This subclass represents a compound expression.
 */

class CompoundExp: public Expression {

public:

    CompoundExp(char op, Expression *lhs, Expression *rhs);
    virtual ~CompoundExp();

    virtual int eval(EvalState & state);
    virtual std::string toString();
    virtual ExpressionType type();

    std::string getOp();
    Expression *getLHS();
    Expression *getRHS();

private:

    std::string op;
    Expression *lhs, *rhs;

};

#endif
```

## `evalstate.h` 接口

```
/*
 * File: evalstate.h
 * ------------------
 * This interface exports the EvalState class, which keeps track of
 * information required by the evaluator, such as the values of variables.
 */

#ifndef _evalstate_h
#define _evalstate_h

#include <string>
#include "map.h"

class EvalState {

public:

    EvalState();
    ~EvalState();
    void setValue(std::string var, int value);
    int getValue(std::string var);
    bool isDefined(std::string var);

private:

    Map<int> symbolTable;

};

#endif
```

## eval 方法的代码

```
int ConstantExp::eval(EvalState & state) {
    return value;
}

int IdentifierExp::eval(EvalState & state) {
    if (!state.isDefined(name)) error(name + " is undefined");
    return state.getValue(name);
}

int CompoundExp::eval(EvalState & state) {
    if (op == "=") {
        if (lhs->getType() != IDENTIFIER) error("Illegal lhs in assignment");
        int val = rhs->eval(state);
        state.setValue(((IdentifierExp *) lhs)->getName(), val);
        return val;
    }
    int left = lhs->eval(state);
    int right = rhs->eval(state);
    if (op == "+") return left + right;
    if (op == "-") return left - right;
    if (op == "*") return left * right;
    if (op == "/") return left / right;
    if (op == "%") return left % right;
    error("Illegal operator in expression");
    return 0;
}
```

## 示例

- 有8个阿拉伯数字，值均为8。现在要用四则运算符 造一批数学表达式，要求每个表达式都等于100（可以使用括号），请写出所有表达式的算法。
- ①任两个阿拉伯数字之间必须有运算符。即不能出现（888+8）/8的情况。
- ②表达式不能有重复。
- ③请写出算法思路及伪代码。

## 结束

