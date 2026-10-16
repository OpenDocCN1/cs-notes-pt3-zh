
## Case study 2. Instrumentation Software

- Display transformers (To_XY and CLIP) convert these waveforms into visual data.
- Component To-XY: converts waveforms into visual data by scaling it and positioning/translating it
- Component Clip: fits the visual data into a display of certain size

## Case study 2. Instrumentation Software

## Parameterized Pipe and Filter Model-structure

- This solution allows user inputs by associating with each filter a control interface that allowed an external entity to set parameters of operation for the filter.
  - For example, the acquisition filter could have parameters that determined **sample rate** and **waveform duration**.
- These inputs serve as configuration parameters for the oscilloscope.

## Parameterized Pipe and Filter Model-structure

- **Looks like each filter has a control panel**
- One can think of such filters as having a "control panel" interface that determines what function will be performed across the conventional input/output dataflow interface Formally.

## Case study 2. Instrumentation Software

## Advantages of Parameterized Pipe and Filter Model

1. **Dynamically modification:** The parameterized pipes-and-filters architecture allows some aspects of the oscilloscope can be modified dynamically by the user.

- It also explains how the user can change oscilloscope functions by incremental adjustments to the software.

## Case study 2. Instrumentation Software

2. **Separation of the user interface:** It separates the signal-processing functions of the oscilloscope from the user interface;

- the signal-processing software makes no assumptions about how the user actually communicates changes to its control parameters.

- Designers can therefore change the implementation of the signal-processing software and hardware without affecting the implementation of the user interface.

## Case study 2. Instrumentation Software

## Disadvantages of Parameterized Pipe and Filter Model

- **poor performance .**
  - **Large storage:** waveforms can occupy a large amount of internal storage, it is simply not practical for each filter to copy waveforms every time they process them.
  - **Bottleneck of slow filter:** Further, different filters may run at radically different speeds: it is unacceptable to slow one filter down because another filter is still processing its data.

## Case study 2. Instrumentation Software

## Solution 3. A Parameterized Pipe-and-Filter
Model with Different Types of Pipes

## Further Specifications

- To handle these problems the model was further specialized. Instead of using a single kind of pipe, we introduced several "colors" of pipes.
  - **No copying some data:** Some of these allowed data to be processed **without copying**.
  - **Ignore incoming data:** Others permitted slow filters to **ignore** incoming data if they were in the middle of processing other data.

## Case study 2. Instrumentation Software

![](img/95717dc23f76db2057b9aa0c49790307_372_0.png)

Oscilloscopes: A Modified Pipe-and-Filter Model with different types of pipes

## Lecture 2. Abstract Factory Pattern

Professor:

Yushan (Michael) Sun

Fall 2016

## Contents of this lecture

- 1. Introduction of the abstract factory pattern
- 2. Theory of the abstract factory pattern
- 3. Design example using the abstract factory pattern
- 4. Further applications of the abstract design pattern

## Introduction of the Abstract Factory Pattern

## Review of the Last Class
上次课复习

## 简单工厂方法模式-汽车保险例子

我的职责是生产对象

![](img/95717dc23f76db2057b9aa0c49790307_377_0.png)

## 工厂方法模式-汽车保险的例子

FactoryGUI

<<Interface>>
PolicyProducer
getPolicyObj()

工厂类

1) 获得产品对象a

2) 调用方法
a. getInsurDescription()

产品类

<<Interface>>
AutoInsurance
getInsurDescription()

BodyInjurPolicyProducer
getPolicyObj()

CollisionPolicyProducer
getPolicyObj()

ComprehensivePolicyProducer
getPolicyObj()

PersonInjuryPolicyProducer
getPolicyObj()

BodyInjurLiability
getInsurDescription

CollisionCoverage
getInsurDescription

ComprehensiveCoverage
getInsurDescription

PersonInjuryProtection
getInsurDescription
