---
layout: post
title: Nand2Tetris Project One
categories: [Nand2Tetris, Computer Science]
tags: [Boolean, Computer Science, Basics, Nand2Tetris]
description: From Boolean algebra to logic gates...
comments: true
---

(Information and Materials for the Nand2Tetris projects comes from The Elements of Computing Systems by Naom Nisan and Shimon Schocken unless otherwise stated.)

The chapter focusses on boolean algebra and its uses in the design and creation of hardware architecture. A boolean function takes binary inputs (e.g. 1 and 0 or yes and No) and outputs a binary value. Every boolean expression can be described using **AND**, **OR** and **NOT** values.

<br/>

>Let's take $x$ and $y$ as our binary variables...
>
>The following notations can be used to express AND, OR, NOT respectively
>
>$xy$ or $x.y$
>
>$x+y$
>
>$\overline{x}$   (The bar denotes NOT)

<br/>

To calculate the number of boolean expressions that can be created from $n$ binary inputs, $2^{2n}$ can be used. Using our example of $x$ and $y$ inputs, this would mean there are 16 boolean expressions which can be created.

Example of a truth table for $f(x,y,z)$ (and bonus python code I wrote!)

<br/>

```python
import pandas as pd

def highlighter(data, color = 'yellow'):
    '''
    highlight the true/1 outputs in a truth table yellow.
    '''
    is_one = data == 1
    return ['background-color: ' + color if v else '' for v in is_one]

truthTable = [{'x': 0, 'y': 0 , 'z':0, 'f(x,y,z)': 0},
              {'x': 0, 'y': 0 , 'z':1, 'f(x,y,z)': 0},
              {'x': 0, 'y': 1 , 'z':0, 'f(x,y,z)': 1},
              {'x': 0, 'y': 1 , 'z':1, 'f(x,y,z)': 0},
              {'x': 1, 'y': 0 , 'z':0, 'f(x,y,z)': 1},
              {'x': 1, 'y': 0 , 'z':1, 'f(x,y,z)': 0},
              {'x': 1, 'y': 1 , 'z':0, 'f(x,y,z)': 1},
              {'x': 1, 'y': 1 , 'z':1, 'f(x,y,z)': 0},]
df = pd.DataFrame(truthTable, columns=['x','y','z','f(x,y,z)'])
#df = df.style.hide_index()
df = df.style.apply(highlighter, subset=['f(x,y,z)']).hide_index()

df
```
<br/>

<style  type="text/css" >
  table {
    width: 100%;
    border-collapse: collapse;
  }
  td, th {
  border: 4px solid #dddddd;
  text-align: left;
  padding: 8px;
}
    #T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow2_col3 {
            background-color:  yellow;
        }    #T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow4_col3 {
            background-color:  yellow;
        }    #T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow6_col3 {
            background-color:  yellow;
        }</style>  
<table id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00c" >
<thead>    <tr>
        <th class="col_heading level0 col0" >x</th>
        <th class="col_heading level0 col1" >y</th>
        <th class="col_heading level0 col2" >z</th>
        <th class="col_heading level0 col3" >f(x,y,z)</th>
    </tr></thead>
<tbody>    <tr>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow0_col0" class="data row0 col0" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow0_col1" class="data row0 col1" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow0_col2" class="data row0 col2" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow0_col3" class="data row0 col3" >0</td>
    </tr>    <tr>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow1_col0" class="data row1 col0" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow1_col1" class="data row1 col1" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow1_col2" class="data row1 col2" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow1_col3" class="data row1 col3" >0</td>
    </tr>    <tr>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow2_col0" class="data row2 col0" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow2_col1" class="data row2 col1" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow2_col2" class="data row2 col2" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow2_col3" class="data row2 col3" >1</td>
    </tr>    <tr>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow3_col0" class="data row3 col0" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow3_col1" class="data row3 col1" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow3_col2" class="data row3 col2" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow3_col3" class="data row3 col3" >0</td>
    </tr>    <tr>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow4_col0" class="data row4 col0" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow4_col1" class="data row4 col1" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow4_col2" class="data row4 col2" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow4_col3" class="data row4 col3" >1</td>
    </tr>    <tr>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow5_col0" class="data row5 col0" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow5_col1" class="data row5 col1" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow5_col2" class="data row5 col2" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow5_col3" class="data row5 col3" >0</td>
    </tr>    <tr>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow6_col0" class="data row6 col0" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow6_col1" class="data row6 col1" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow6_col2" class="data row6 col2" >0</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow6_col3" class="data row6 col3" >1</td>
    </tr>    <tr>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow7_col0" class="data row7 col0" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow7_col1" class="data row7 col1" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow7_col2" class="data row7 col2" >1</td>
        <td id="T_ccd243a6_9d31_11ea_b7d3_509a4ccea00crow7_col3" class="data row7 col3" >0</td>
    </tr></tbody>
</table>

<br/>

Using the expressions which equal to 1, we can start to create the canonical representation of our truth table.

<br/>
>
>
>**OR** $y$
>**OR** $x$
>**NOT** $z$
>
>Thus the canonical representation is $(x + y).z$

<br/>

Boolean algebra can be used to define the logic of a **gate**. A gate will enact this logic, to give the required binary output. Transistors are switching devices which can be used to enact the overall gate logic. These are installed on silicon to create computer chips. Gates can be separated into **primitive** gates (only carry out simple logic operations) or **composite** gates (made up of multiple primitive gates to effect more complex boolean logic). Below are examples of logic gate symbology and how they can be chained together to create composite gates.

<br/>
![png](/assets/jupyter/logic_diagram_example.png){:.center-image}
<p style="text-align: center;">Figure 1: These are the standard diagrams used to denote the basic logic gates</p>

<br/>
