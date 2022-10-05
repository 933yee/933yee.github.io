---
title: Expressions
date: 2022-10-05 14:01:00 +0800
categories: [Code, Others, Expressions]
tags: [expressions]     # TAG names should always be lowercase
math: true
---

**Infix**
===

- ### Property
    - Operator comes in-between the operands.
    - Hard to evaluate using codes.

<br>

**Postfix**
===

- ### Property
    - Each operator appears after its operands.
    - No need <span style="color:red"> parentheses </span>.
    - Priority of operators is no longer relevant.
    - Expression can be efficiently evaluated by
        1. Making a left to right scan.
        2. <span style="color:red"> Stacking </span> operands.
        3. Evaluating operators.
        4. Push the result into stack.

- ### Example
    - A B + C -
        1. push A
        2. push B
        3. *(detecting an operator)* pop two operands out and push the result after calculating them
        4. push C
        5. *(detecting an operator)* pop two operands out and push the result after calculating them
<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
The result is <span style="color:red"> (A + B) - C </span>.

<br>

![postfix1](/assets/images/postfix1.png)

**Conversion**
===

- ### Infix to Postfix
    - Rules
        - Because <span style="color:red"> the order of operands does not change </span>, we can just output every visting operand directly.
        - Utilize <span style="color:red"> stack </span> to store operators.
        - When the **priority** of operator on top of stack is <span style="color:red"> higher or equal to </span> that of the <span style="color:red"> incoming </span> operator, pop the operands in stack out.
        - If the expression includes parentheses, follow the rules below:
            1. ' ( ' has the highest priority, <span style="color:red"> always push to stack </span>.
            2. Once pushed, ' ( ' get lowest priority.
            3. Pop the operators in stack once you see the matched ' ) '. <br>
    That is, <span style="color:red">**' ( ' never pops other operators and never gets popped unless seeing a ' ) '** </span>

    - Example
        - A + B * C
            <br>
            ![postfix2](/assets/images/postfix2.png){: width="400" , height = "500"}
        <br>

        - A * (B + C) * D
            <br>
            ![postfix3](/assets/images/postfix3.png){: width="400" , height = "550"}

