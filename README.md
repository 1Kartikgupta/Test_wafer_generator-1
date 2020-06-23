# Test_wafer_generator
  This project is divided in three parts
1.	Placement of the Test Cell: Putting the standard cell in the middle and place the test cells around the standard cell with equal spacing around them. Then connecting the standard cell with the test cell with metal contact in an automated manner. This is can be done by any of the programming language like Perl, Python, etc with the help of layout tool Magic. Fig.
2.	 Placement of all the Standard Cell in Die
3.	Automatic test Pattern Generator: After placement and routing of all the  elements in the die we now test our wafer using a ATPG with the help of a wafer probing machine. This test pattern generator can be designed with help of perl programming.

The Atpg tool is an electronic design automation method/technology which is used to find an input or test sequence that when applied to a wafer containing a digital circuit, enables ATE to distinguish between the correct circuit behavior and the errors caused by the defects present in wafer. This used for failure analysis which is used to test semiconductor devices after manufacture or to assist with determining the cause of failure. By the number of modeled defects or fault models which is detectable by the number of generated pattern the effectiveness of ATPG can be measured 

The Atpg tool which will help to detect the errors in the circuit is known as Atlanta version 2.0. For further details you can visit the github repository : https://github.com/hsluoyz/Atalanta
This is a an automatic test pattern generator for stuck at faults in combinational circuit developed bythe Bradley Department of Electrical and Computer Enginnering, Virginia Polythechnic Institute & State University. 

We have requested them to make this tool open-source so that everyone can work on it and build a more better environment

Before this to check the golden Response of the circuit we have to check with the help of truth table

# Truth Table generator

truth-table-generator is a tool that allows to generate a truth table. It is a fork of truths by tr3buchet.

# Steps for installing truth table using python
```
pip install truth-table-generator
```
# Usage

First, let's import the package. ```ttg``` stands for truth-table-generator
```
import ttg 
```
A truth table has one column for each input variable (for example, p and q), and one final column showing all of the possible results of the logical operation that the table represents. If the input has only one list of strings, each string is considered an input variable:
```
print(ttg.Truths(['p', 'q', 'r']))
```
```
+-----+-----+-----+
|  p  |  q  |  r  |
|-----+-----+-----|
|  1  |  1  |  1  |
|  1  |  1  |  0  |
|  1  |  0  |  1  |
|  1  |  0  |  0  |
|  0  |  1  |  1  |
|  0  |  1  |  0  |
|  0  |  0  |  1  |
|  0  |  0  |  0  |
+-----+-----+-----+
```
A second list of strings can be passed with propositional expressions created with logical operators.
```
print(ttg.Truths(['p', 'q', 'r'], ['p and q and r', 'p or q or r', '(p or (~q)) => r']))
```
```
+-----+-----+-----+-----------------+---------------+--------------------+
|  p  |  q  |  r  |  p and q and r  |  p or q or r  |  (p or (~q)) => r  |
|-----+-----+-----+-----------------+---------------+--------------------|
|  1  |  1  |  1  |        1        |       1       |         1          |
|  1  |  1  |  0  |        0        |       1       |         0          |
|  1  |  0  |  1  |        0        |       1       |         1          |
|  1  |  0  |  0  |        0        |       1       |         0          |
|  0  |  1  |  1  |        0        |       1       |         1          |
|  0  |  1  |  0  |        0        |       1       |         1          |
|  0  |  0  |  1  |        0        |       1       |         1          |
|  0  |  0  |  0  |        0        |       0       |         0          |
```
Operators and their representations:
negation: ```'not'```,``` '-'```, ```'~'```
logical disjunction: ```'or'```
logical nor: ```'nor'```
exclusive disjunction: ```'xor'```, ```'!='```
logical conjunction: ```'and'```
logical NAND: ```'nand'```
material implication: ```'=>'```, ```'implies'```
logical biconditional: ```'='```
Note: Use parentheses! Especially with the negation operator. Use tables above and below as reference. Although precedence rules are used, sometimes precedence between conjunction and disjunction is unspecified requiring to provide it explicitly in given formula with parentheses.

