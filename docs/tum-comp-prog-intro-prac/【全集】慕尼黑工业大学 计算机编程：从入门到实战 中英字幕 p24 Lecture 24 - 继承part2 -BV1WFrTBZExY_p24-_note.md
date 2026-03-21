# 慕尼黑工业大学 计算机编程：从入门到实战：24：继承（第二部分）

![](img/eb82cbce05758530c1a08f1e5ecf5eec_1.png)

在本节课中，我们将继续深入学习继承的概念，并通过更复杂的例子来理解其在实际编程中的应用。我们将探讨作用域、绑定、方法重写等关键主题，并构建一个模拟银行账户系统的程序来实践这些概念。

---

## 继承示例：食物与披萨

上一节我们介绍了继承的基本概念，本节中我们来看看一个具体的例子。这个程序名为“eating”，目标是计算每餐食物的卡路里。

我们有一个超类 `Food` 和一个子类 `Pizza`。在 `Food` 类中，我们定义了三个整型变量：一个常量 `caloriesPerGram`（值为9），以及变量 `fat` 和 `servings`。这些变量在构造函数中初始化。

```java
public class Food {
    private final int caloriesPerGram = 9;
    private int fat;
    private int servings;

    public Food(int fat, int servings) {
        this.fat = fat;
        this.servings = servings;
    }

    private int calories() {
        return fat * caloriesPerGram;
    }

    public int caloriesPerServing() {
        return calories() / servings;
    }
}
```

`calories` 方法是私有的，用于计算总卡路里。`caloriesPerServing` 方法是公共的，它调用私有方法并除以份数来得到每份的卡路里。

`Pizza` 类继承自 `Food`。它没有默认构造函数，因此必须提供一个构造函数。我们假设一个披萨总是被切成8份，所以 `servings` 固定为8，而脂肪含量则根据披萨类型传入。

```java
public class Pizza extends Food {
    public Pizza(int fat) {
        super(fat, 8); // 披萨总是8份
    }
}
```

现在，我们可以创建程序并使用它。

```java
public class Eating {
    public static void main(String[] args) {
        Pizza specialPizza = new Pizza(275);
        System.out.println(specialPizza.caloriesPerServing());
    }
}
```

当我们调用 `specialPizza.caloriesPerServing()` 时，由于该方法是公共的，子类可以继承并使用它。这个方法内部会调用超类的私有 `calories` 方法。虽然子类不能直接访问私有成员，但通过公共方法可以间接地进行计算。程序将输出每份的卡路里值（例如309）。

这个例子展示了信息隐藏：只有特定的公共元素对子类和程序的其他部分可见，但通过调用方法，我们可以间接访问和计算私有数据。

---

## 绑定与作用域

在深入讨论继承如何影响作用域和绑定之前，我们需要理解这两个基本概念。

**绑定** 指的是将一个表达式（如变量名）关联到内存中的一个特定变量或属性。
**作用域** 指的是程序中该绑定有效的区域。在Java等语言中，作用域通常由花括号 `{}` 界定。

以下是作用域的几个例子：

*   **局部变量**：从变量声明处开始，到其所在的代码块（由 `{}` 界定）结束为止。
*   **方法参数**：仅在方法体内有效。
*   **静态变量**：具有全局作用域，在整个应用程序中可访问。

考虑我们之前实现的 `Queue` 类：

```java
public class Queue {
    private int first;
    private int last;
    private int[] array;

    public void enqueue(int x) {
        // 参数 x 的作用域仅限于此方法内
        array[last] = x;
        last++;
    }

    public void someMethod() {
        for (int i = 0; i < 10; i++) { // 变量 i 的作用域仅限于此 for 循环内
            // 使用 i
        }
        // 此处无法访问 i
    }
}
```

类属性 `first`、`last`、`array` 的作用域是整个类。方法参数 `x` 的作用域仅限于 `enqueue` 方法内。`for` 循环中声明的计数器 `i` 的作用域仅限于该循环内部。

理解作用域和绑定对于掌握继承中的一些特性至关重要。

---

## 继承中的阴影

在继承中，可能会遇到“阴影”的情况。这意味着在某个作用域内已经存在一个绑定，但你又用相同的名字声明了一个新的绑定。

### 属性阴影

当超类和子类定义了同名的属性时，就会发生属性阴影。子类中的属性会“遮蔽”超类中的同名属性。

```java
class Person {
    public int age;
}

class Child extends Person {
    public int age; // 阴影了超类的 age 属性
    public void setPersonAge(int a) {
        super.age = a; // 使用 super 关键字访问超类的 age
    }
}
```

虽然Java允许这样做，但这被认为是**糟糕的实践**，因为它极易导致混淆。你可以使用 `super` 关键字来明确指定要访问超类的属性。但更好的做法是避免使用相同的属性名。

### 方法阴影（重写）

当子类重新定义了超类中已有的方法（具有相同名称和参数列表）时，就发生了方法阴影，这通常被称为**方法重写**。

```java
class Person {
    public int getAge() {
        return age;
    }
}

class Child extends Person {
    @Override // 使用注解明确表示这是重写
    public int getAge() {
        return this.age; // 这里返回的是子类的 age 属性
    }
}
```

方法重写是面向对象编程中常见且有用的技术。在运行时，Java虚拟机会首先查看对象的实际类型（子类），如果存在重写的方法，则调用它；否则，才会调用超类中的方法。

**重要区别**：属性阴影应避免，而方法重写（在遵循里氏替换原则的前提下）是合理且常用的。

---

## 综合示例：银行账户系统

为了综合练习继承，我们来构建一个模拟银行账户系统的程序。我们将创建几种不同类型的账户。

### 基类：BankAccount

首先，定义所有账户的基类 `BankAccount`。每个账户有一个ID和一个余额。

```java
public class BankAccount {
    private final int accountId;
    private double balance;

    public BankAccount(int accountId, double initialBalance) {
        this.accountId = accountId;
        this.balance = initialBalance;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Account " + accountId + ": Deposited " + amount + ". New balance: " + balance);
    }

    public boolean withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Account " + accountId + ": Insufficient funds.");
            return false;
        }
        balance -= amount;
        System.out.println("Account " + accountId + ": Withdrew " + amount + ". New balance: " + balance);
        return true;
    }
}
```

`deposit` 方法用于存款，`withdraw` 方法用于取款。取款时会检查余额是否充足。

### 子类：SavingsAccount

`SavingsAccount` 继承自 `BankAccount`，并增加了利率的概念。

```java
public class SavingsAccount extends BankAccount {
    private final double interestRate;

    public SavingsAccount(int accountId, double initialBalance, double interestRate) {
        super(accountId, initialBalance);
        this.interestRate = interestRate;
    }

    public void addInterest() {
        double interest = getBalance() * interestRate; // 假设有 getBalance() 方法
        deposit(interest); // 利用继承的 deposit 方法
        System.out.println("Account " + getAccountId() + ": Interest added. New balance: " + getBalance());
    }
}
```

`SavingsAccount` 继承了存款和取款功能，并新增了 `addInterest` 方法来计算和添加利息。

### 子类：CheckingAccount

`CheckingAccount`（支票账户）更复杂一些。它可以关联一个 `SavingsAccount` 作为透支保护。

```java
public class CheckingAccount extends BankAccount {
    private final SavingsAccount overdraft;

    public CheckingAccount(int accountId, double initialBalance, SavingsAccount overdraft) {
        super(accountId, initialBalance);
        this.overdraft = overdraft;
    }

    @Override
    public boolean withdraw(double amount) {
        // 1. 先尝试从本账户取款
        if (super.withdraw(amount)) {
            return true;
        }
        // 2. 如果本账户余额不足，计算差额并从透支账户中尝试取款
        double shortfall = amount - getBalance();
        if (overdraft.withdraw(shortfall)) {
            // 透支成功，将本账户余额设为0，因为已全部取出
            // 注意：这里需要直接操作余额，可能需要将 balance 设为 protected 或提供 setter
            setBalance(0);
            System.out.println("Overdraft used. Checking account balance: 0. Overdraft balance: " + overdraft.getBalance());
            return true;
        } else {
            System.out.println("Overdraft source insufficient.");
            return false;
        }
    }
}
```

`CheckingAccount` **重写**了 `withdraw` 方法。它首先尝试调用超类的取款逻辑。如果失败（余额不足），则尝试从关联的 `overdraft`（储蓄账户）中取出差额。

### 子类：BonusSaverAccount

`BonusSaverAccount` 继承自 `SavingsAccount`，它提供更高的利率，但如果提前取款则会收取罚金。

```java
public class BonusSaverAccount extends SavingsAccount {
    private final double penaltyRate;
    private final double bonusInterestRate;

    public BonusSaverAccount(int accountId, double initialBalance, double baseInterestRate, double penaltyRate, double bonusInterestRate) {
        super(accountId, initialBalance, baseInterestRate);
        this.penaltyRate = penaltyRate;
        this.bonusInterestRate = bonusInterestRate;
    }

    @Override
    public boolean withdraw(double amount) {
        double amountWithPenalty = amount * (1 + penaltyRate);
        System.out.println("Penalty incurred. Attempting to withdraw: " + amountWithPenalty);
        return super.withdraw(amountWithPenalty);
    }

    @Override
    public void addInterest() {
        // 使用更高的奖金利率计算利息
        double interest = getBalance() * bonusInterestRate;
        deposit(interest);
        System.out.println("Bonus interest added.");
    }
}
```

它重写了 `withdraw` 方法，在取款金额上增加了罚金。同时也重写了 `addInterest` 方法，使用更高的奖金利率。

### 类图与使用

以下是这些类之间关系的简化UML类图：

```
BankAccount
├── SavingsAccount
│   └── BonusSaverAccount
└── CheckingAccount
```

*   `BankAccount` 是基类。
*   `SavingsAccount` 和 `CheckingAccount` 继承自 `BankAccount`。
*   `BonusSaverAccount` 继承自 `SavingsAccount`。
*   `CheckingAccount` 与一个 `SavingsAccount` 关联（作为透支账户）。

使用示例：

```java
public class BankDemo {
    public static void main(String[] args) {
        SavingsAccount savings = new SavingsAccount(1, 5000, 0.01);
        BonusSaverAccount bonusSavings = new BonusSaverAccount(2, 1000, 0.01, 0.25, 0.04);
        CheckingAccount checking = new CheckingAccount(3, 100, savings);

        savings.deposit(176); // 存款
        bonusSavings.withdraw(120); // 取款，会触发罚金
        checking.withdraw(600); // 取款，余额不足，会使用储蓄账户透支
    }
}
```

**继承的强大之处**：注意 `CheckingAccount` 的构造函数接受一个 `SavingsAccount` 类型参数。由于继承，我们可以传入任何 `SavingsAccount` 的子类，例如 `BonusSaverAccount`。代码仍然可以工作，只是行为会根据子类的特定实现（如取款罚金）而略有变化。这种可替换性是代码复用的强大工具。

---

## 练习：实现 CreditCardAccount

现在，请你尝试创建一个新的子类 `CreditCardAccount`。

**核心要求**：
1.  `CreditCardAccount` 应继承自 `BankAccount`。
2.  它需要追踪一个“信用余额”（`creditBalance`）。正常取款/消费会使此值变为负数（表示欠款）。
3.  它应有一个信用`limit`（额度），消费不能使 `-creditBalance` 超过此额度。
4.  实现一个 `pay(double amount)` 方法来进行消费。如果消费后欠款超过额度，则交易失败。
5.  在 `main` 方法中创建 `CreditCardAccount` 对象并测试 `pay` 方法。

**可选挑战**：
1.  实现一个 `compensate()` 方法，每月调用一次，用于从关联的 `CheckingAccount` 中扣款来偿还信用欠款（`creditBalance`）。偿还后，`creditBalance` 归零。
2.  实现一个 `handleOverdraftInterest()` 方法，如果偿还欠款后 `CheckingAccount` 的余额变为负数，则收取高额透支利息。

---

## 示例解决方案框架

以下是 `CreditCardAccount` 的一个可能实现框架：

```java
public class CreditCardAccount extends BankAccount {
    private final double limit;
    private double creditBalance;

    public CreditCardAccount(int accountId, double initialBalance, double limit) {
        super(accountId, initialBalance);
        this.limit = limit;
        this.creditBalance = 0;
    }

    public boolean pay(double amount) {
        if (-creditBalance + amount > limit) {
            System.out.println("Payment declined: Over credit limit.");
            return false;
        }
        creditBalance -= amount; // 信用余额减少（变为更负的数值）
        System.out.println("Payment of " + amount + " processed. Credit balance: " + creditBalance);
        return true;
    }

    // 可选挑战1：补偿方法
    public void compensate(CheckingAccount checkingAccount) {
        double amountToCompensate = -creditBalance; // 欠款总额是正数
        if (checkingAccount.withdraw(amountToCompensate)) {
            creditBalance = 0;
            System.out.println("Credit card compensated. New checking balance: " + checkingAccount.getBalance());
        } else {
            System.out.println("Compensation failed: Insufficient funds in checking account.");
        }
    }

    // 可选挑战2：处理透支利息
    public void handleOverdraftInterest(BankAccount account, double overdraftInterestRate) {
        if (account.getBalance() < 0) {
            double interest = -account.getBalance() * overdraftInterestRate;
            // 假设有一个 applyFee 方法或直接操作余额
            System.out.println("Overdraft interest applied: " + interest);
            // account.balance -= interest; // 需要访问权限
        }
    }
}
```

测试代码示例：

```java
public static void main(String[] args) {
    CreditCardAccount creditCard = new CreditCardAccount(4, 0, 1000); // 初始余额0，额度1000
    CheckingAccount checking = new CheckingAccount(5, 500, null);

    creditCard.pay(300);
    creditCard.pay(400);
    creditCard.pay(299); // 总共 999，成功
    creditCard.pay(2);   // 总共 1001，超过1000额度，失败

    creditCard.compensate(checking); // 从支票账户偿还999
    // 此时 checking 账户余额为 500 - 999 = -499
    creditCard.handleOverdraftInterest(checking, 0.05); // 收取5%透支利息
}
```

---

## 总结

本节课中我们一起深入学习了继承的多个重要方面：

1.  **通过“食物与披萨”示例**，我们巩固了继承的基本用法，理解了公共方法如何提供对私有数据的间接访问。
2.  **学习了绑定与作用域**，明确了变量在程序不同部分的有效范围，这是理解更复杂概念的基础。
3.  **区分了属性阴影与方法重写**：属性阴影（应避免）会创建同名的不同变量；方法重写（合理使用）是子类提供特定实现的方式，运行时根据对象实际类型调用对应方法。
4.  **构建了完整的银行账户系统**，实践了继承层次结构的设计，包括 `BankAccount`、`SavingsAccount`、`CheckingAccount` 和 `BonusSaverAccount`。我们看到了如何重写方法以改变行为，以及如何通过关联对象（如透支账户）实现更复杂的功能。
5.  **完成了 `CreditCardAccount` 的实现练习**，应用所学知识来扩展系统。

![](img/eb82cbce05758530c1a08f1e5ecf5eec_3.png)

继承是面向对象编程的支柱之一，它支持代码复用、扩展和组织。理解如何正确设计类层次结构以及方法重写的机制，对于构建可维护、可扩展的软件至关重要。