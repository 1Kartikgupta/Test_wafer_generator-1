# Test_wafer_generator
  This project is divided in three parts
1.	Placement of the Test Cell: Putting the standard cell in the middle and place the test cells around the standard cell with equal spacing around them. Then connecting the standard cell with the test cell with metal contact in an automated manner. This is can be done by any of the programming language like Perl, Python, etc with the help of layout tool Magic.
<img src= "https://github.com/Abhiram504/Test_wafer_generator/blob/master/WhatsApp%20Image%202020-06-15%20at%208.53.14%20PM.jpeg?raw=true">

2.	 Placement of all the Standard Cell in Die
<img src="https://github.com/Abhiram504/Test_wafer_generator/blob/master/WhatsApp%20Image%202020-06-15%20at%208.45.23%20PM.jpeg?raw=true">

<img src="https://github.com/Abhiram504/Test_wafer_generator/blob/master/WhatsApp%20Image%202020-06-15%20at%208.47.15%20PM.jpeg?raw=true">

3.	Automatic test Pattern Generator: After placement and routing of all the  elements in the die we now test our wafer using a ATPG with the help of a wafer probing machine. This test pattern generator can be designed with help of perl programming.

The Atpg tool is an electronic design automation method/technology which is used to find an input or test sequence that when applied to a wafer containing a digital circuit, enables ATE to distinguish between the correct circuit behavior and the errors caused by the defects present in wafer. This used for failure analysis which is used to test semiconductor devices after manufacture or to assist with determining the cause of failure. By the number of modeled defects or fault models which is detectable by the number of generated pattern the effectiveness of ATPG can be measured 

The Atpg tool which will help to detect the errors in the circuit is known as Atlanta version 2.0. For further details you can visit the github repository : https://github.com/hsluoyz/Atalanta
This is a an automatic test pattern generator for stuck at faults in combinational circuit developed bythe Bradley Department of Electrical and Computer Enginnering, Virginia Polythechnic Institute & State University. 

We have requested them to make this tool open-source so that everyone can work on it and build a more better environment

# Let's Start
.Installing Python3, Ngspice, Z3 Solver
.Creating a python virtual environment
.Installing librecell using git
.Applying Conversion Commands
.Installing MAGIC To see Layout

# Downloading Python3, Ngspice, Z3 Solver
For Ubuntu using terminal window we will download the required tools 

To install python 3 the command is 
```
sudo apt-get install python3
```
Commands to install Ngspice and Z3
```
sudo pacman -S install ngspice z3
```
We will require MAGIC software to read the ```.mag``` files
```
sudo apt-get install magic
```
To check whether all the tools are installed : try for checkpoints
Checkpoint 1: type ```python3```for python, enter command ```z3--help``` for z3 solver Give command ```ngspice``` for ngspice

Now we need to work on thr python working environment
use the foloowing commands for setting up your python virtual environment
```
python3 -m venv my-librecell-env
source ./my-librecell-env/bin/activate
```
# Installing Librecell
WE will install libre cell from git so use the following command to download and install
```
git clone https://codeberg.org/tok/librecell.git
cd librecell
```
```
cd librecell-common
python3 setup.py develop
cd ..
```
```
cd librecell-layout
python3 setup.py develop
cd ..
```
```
cd librecell-lib
python3 setup.py develop
cd ..
```
To make sure that the libre cell is installed properly typre the foloowing command
```
librecell --h
```
If terminal is showing information or help commands then librecell is installed.

Next we need to deal with actual files that is spice netlist files, tech files, directories,etc. We need to make directory in lbrecell layout folder. Make sure that you are in librecell folder right now [From librecell folder we will go to librecell-layout]
```
cd librecell-layout
```
So make a directory
```
mkdir /tmp/mylibrary
```

After this to check the golden Response of the circuit we have to check with the help of truth table

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

