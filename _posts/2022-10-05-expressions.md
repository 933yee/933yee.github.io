---
title: Expressions
date: 2022-10-05 14:01:00 +0800
categories: [Code, Others, Expressions]
tags: [expressions]     # TAG names should always be lowercase
math: true
---
**Infix**
===

- ## Property
    - Operator comes in-between the operands.
    - Ambiguous. Need **parentheses** to make them unambiguous.
    - Hard to evaluate using codes.

---

**Postfix**
===

- ## Property
    - Each operator appears after its operands.
    - No need <span style="color:red"> parentheses </span>.
    - Priority of operators is no longer relevant.
    - Postfix notations can be used in intermediate code generation in compiler design.
    - Easier to parse for a machine.
- ## Evaluation
    - Step
        1. Making a left to right scan.
        2. <span style="color:red"> Stacking </span> operands.
        3. Evaluating operators.
        4. Push the result into stack.
    - Example
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

---

**Prefix**
===
- ## Property
    - Each operator appears before its operands.
    - No need <span style="color:red"> parentheses </span>.
    - Priority of operators is no longer relevant.
    - Prefix notations are used in many programming languages like LISP.
    - Easier to parse for a machine.
- ## Evaluation
    - Step
        The same as evaluating postfix, but read from <span style="color:red"> **right to left** </span>
    - Example
        - / A * B C 
            1. push C
            2. push B
            3. *(detecting an operator)* pop two operands out and push the result after calculating them
            4. push A
            5. *(detecting an operator)* pop two operands out and push the result after calculating them
            
<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
The result is <span style="color:red"> A / (B * C) </span>.

**Conversion**
===

- ## Infix to Postfix
    - Rules
        - Because <span style="color:red"> the order of operands does not change </span>, we can just output every visting operand directly.
        - Utilize <span style="color:red"> stack </span> to store operators.
        - When the **priority** of the operator on top of the stack is <span style="color:red"> higher or equal to </span> that of the <span style="color:red"> incoming </span> operator, pop the operator in stack out.
        - If the expression includes parentheses, follow the steps below:
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
            
- ## Infix to Prefix
    - Steps
        1. Reverse the infix expression.
        2. Apply a modified infix to postfix algorithm on reversed input.<span style="color:red">(But do not pop the operator out if its priority is equal to the incoming operator.)<span>
        3. Reverse the output
    
    - Example
        - 1 + ( 3 * 4 – 5 ) / 6 * 7
            <br>
            ![prefix1](/assets/images/prefix1.png){: width="400" , height = "600"}

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
The result is <span style="color:red"> + 1 * / - * 3 4 5 6 7 </span>.

- ## Postfix to Infix
- ## Postfix to Infix
