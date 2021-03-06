# Tower of Hanoi

*******
# Writer Intro

I am **Subham Maity.**

I love Programming. One of the aims I had when I started ```CodeXam``` was to make learning programming easy.**

**At ```CodeXam```, we ask ourselves one question every day: "How do we create awesome learning experiences?"**

### Help us improve this guide - Fork, Pull Requests, Shares and Likes are recommended!
*******
## Chapters
* [What is Tower of Hanoi](#what-is-tower-of-hanoi)
* [Rules](#rules)
* [Algorithm](#algorithm)
* [Code Remember Tip](#code-remember-tips)
* [java Code](#java-code)
* [Detailed Visualization](#detailed-visualization)
* [Time Complexity](#time-complexity)
#### Other Language Code
* [C++](#c-plus)
* [java](#java)
* [Python](#python)
* [C#](#c-sharp)
* [PHP](#php)
* [Javascript](#javascript)
#### Recursion Details 
* [Recursion Learn here](#recursion-learn-here)

*******
#### What is Tower of Hanoi
**Tower of Hanoi is a mathematical puzzle where we have three rods and n disks. The objective of the puzzle is to move the entire stack to another rod, obeying the following simple rules:**
#### Rules
```javascript
1.Only one disk can be moved at a time.

2.Each move consists of taking the upper disk from one of the stacks and placing
 it on top of another stack i.e. a disk can only be moved if it is the uppermost disk on a stack.
 
3.No disk may be placed on top of a smaller disk.
```

#### Algorithm


Step 1:
If we have only one disk we considered it as n =1 so
transferring process will easy in this process
one is **Source(S)** and 2nd one is **Head(H)** and then last one is **Destination(D)**

<p align="center">
        <img src="https://github.com/Subham-Maity/java-recursion-and-backtracking/blob/master/image(ignore)/th1.png?raw=true"/>
        </p>

Step 2:
If we have only two disk we considered it as n =2 so
transferring process will easy in this process
one is **Source(S)** and 2nd one is **Head(H)/Auxiliary** and then last one is **Destination(D)**

<p align="center">
        <img src="https://github.com/Subham-Maity/java-recursion-and-backtracking/blob/master/image(ignore)/towerofhanoi2.gif?raw=true"/>
        </p>

Step 3:
If we have only three disk we considered it as n = 3 so
transferring process will easy in this process
one is **Source(S)** and 2nd one is **Head(H)/Auxiliary** and then last one is **Destination(D)**

```javascript

Let rod 1 = 'A', rod 2 = 'B', rod 3 = 'C'.
An example with 2 disks :
Step 1 : Shift first disk from 'A' to 'B'.

Step 2 : Shift second disk from 'A' to 'C'.

Step 3 : Shift first disk from 'B' to 'C'.
An example with 3 disks :
Step 1 : Shift first disk from 'A' to 'C'.
Step 2 : Shift second disk from 'A' to 'B'.
Step 3 : Shift first disk from 'C' to 'B'.

Step 4 : Shift third disk from 'A' to 'C'.

Step 5 : Shift first disk from 'B' to 'A'.
Step 6 : Shift second disk from 'B' to 'C'.
Step 7 : Shift first disk from 'A' to 'C'.

(Notice the gaps)
The pattern here is :
 - Shift 'n-1' disks from 'A' to 'B', using C.
 - Shift last disk from 'A' to 'C'.
 - Shift 'n-1' disks from 'B' to 'C', using A.
```
<p align="center">
        <img src="https://github.com/Subham-Maity/java-recursion-and-backtracking/blob/master/image(ignore)/stackheight3.jpeg?raw=true"/>
        </p>

#### **Code Remember Tips**
```javascript
main format for getting parameters -> src, helper, dest
call -> n-1 transfet ->  src, dest, helper
print -> ("disk " + n + " from " + src + " to " + helper);
call -> n-1 transfet -> dest, helper, src
Passing parameters -> src,  dest , helper
```
#### java Code
```java
public class CodeXam {
    public static void towerOfHanoi(int n, String src, String helper, String dest) {
        if(n == 0) {
            return;
        }
    /*1. Imagine that one disk is present in the tower of hanoi, so once that disk passes directly from the source to the destination
    (as seen in the first image you can check it out.)
    2. In the first place, you can see that I'm stating here n-1 disk transfer source to helper, which means we're assuming we have three disks.
    Now remain one disk in the source, and already we transfer two disks to the helper so both are ours (n-1) [n-1 = 2 because 1 disk + (n-1) disk = n disk]
    and (it may be possible in that case there have been many steps taken in that transfer process) you can check the image below -> step 4
    * */
// top n-1 from src to helper using dest as 'helper'
        towerOfHanoi(n-1, src, dest, helper);
//transfer nth from src to dest
        System.out.println("transfer disk " + n + " from " + src + " to " + helper);
//transfer n-1 from helper to dest using src as 'helper'
        towerOfHanoi(n - 1, dest, helper, src);
    }
    public static void main(String args[]) {
        int n = 3;
        towerOfHanoi(n, "S", "D", "H");
    }
}
```


#### Output:

```javascript
transfer disk 1 from S to D
transfer disk 2 from S to H
transfer disk 1 from D to H
transfer disk 3 from S to D
transfer disk 1 from H to S
transfer disk 2 from H to D
transfer disk 1 from S to D

```
#### Detailed Visualization:
<p align="center">
        <img src="https://github.com/Subham-Maity/java-recursion-and-backtracking/blob/master/image(ignore)/towerofhanoi.png?raw=true"/>
        </p>

#### **Time Complexity**
<p align="center">
        <img src="https://github.com/Subham-Maity/java-recursion-and-backtracking/blob/master/image(ignore)/timecomplexity%20.jpg?raw=true"/>
        </p>



## C Plus 
## C++ 
```cpp
// C++ recursive function to
// solve tower of hanoi puzzle
#include <bits/stdc++.h>
using namespace std;
 
void towerOfHanoi(int n, char from_rod,
                    char to_rod, char aux_rod)
{
    if (n == 0)
    {
        return;
    }
    towerOfHanoi(n - 1, from_rod, aux_rod, to_rod);
    cout << "Move disk " << n << " from rod " << from_rod <<
                                " to rod " << to_rod << endl;
    towerOfHanoi(n - 1, aux_rod, to_rod, from_rod);
}
 
// Driver code
int main()
{
    int n = 4; // Number of disks
    towerOfHanoi(n, 'A', 'C', 'B'); // A, B and C are names of rods
    return 0;
}
 
```
## java
```java
// JAVA recursive function to
// solve tower of hanoi puzzle
import java.util.*;
import java.io.*;
import java.math.*;
class CodeXam
{
static void towerOfHanoi(int n, char from_rod,
                    char to_rod, char aux_rod)
{
    if (n == 0)
    {
        return;
    }
    towerOfHanoi(n - 1, from_rod, aux_rod, to_rod);
    System.out.println("Move disk "+ n + " from rod " +
                       from_rod +" to rod " + to_rod );
    towerOfHanoi(n - 1, aux_rod, to_rod, from_rod);
}
 
// Driver code
public static void  main(String args[])
{
    int n = 4; // Number of disks
    towerOfHanoi(n, 'A', 'C', 'B'); // A, B and C are names of rods
}
}
```
## Python
```py
# Recursive Python function to solve tower of hanoi
 
def TowerOfHanoi(n , from_rod, to_rod, aux_rod):
    if n == 0:
        return
    TowerOfHanoi(n-1, from_rod, aux_rod, to_rod)
    print("Move disk",n,"from rod",from_rod,"to rod",to_rod)
    TowerOfHanoi(n-1, aux_rod, to_rod, from_rod)
         
# Driver code
n = 4
TowerOfHanoi(n, 'A', 'C', 'B')
# A, C, B are the name of rods
```
## C Sharp 
## C#
```cs

// C# recursive program to solve tower of hanoi puzzle
using System;
class CodeXam
{
    static void towerOfHanoi(int n, char from_rod, char to_rod, char aux_rod)
    {
        if (n == 0)
        {
            return;
        }
        towerOfHanoi(n-1, from_rod, aux_rod, to_rod);
        Console.WriteLine("Move disk " + n + " from rod " + 
                          from_rod + " to rod " + to_rod);
        towerOfHanoi(n-1, aux_rod, to_rod, from_rod);
    }
     
    //  Driver method
    public static void Main(String []args)
    {
        int n = 4; // Number of disks
        towerOfHanoi(n, 'A', 'C', 'B');  // A, B and C are names of rods
    }
}
```
## PHP
```php
<?php
 
// Tower of Hanoi (n-disk) algorithm in PHP with Display of Pole/rod
// Contents the 3 poles representation
$poles = array(array(), array(), array());
 
function TOH($n, $A="A", $B="B", $C="C"){
     
    if ($n > 0){
        TOH($n-1, $A, $C, $B);
        echo "Move disk from rod $A to rod $C \n";
        move($A, $C);
        dispPoles();
        TOH($n-1, $B, $A, $C);
    }
    else {
        return;
    }
}
 
function initPoles($n){
    global $poles;
 
    for ($i=$n; $i>=1; --$i){
        $poles[0][] = $i;
    }
}
 
 
function move($source, $destination){
    global $poles;
     
    // get source and destination pointers
    if ($source=="A") $ptr1=0;
    elseif ($source=="B") $ptr1 = 1;
    else $ptr1 = 2;
     
    if ($destination=="A") $ptr2 = 0;
    elseif ($destination=="B") $ptr2 = 1;
    else $ptr2 = 2;
     
    $top = array_pop($poles[$ptr1]);
    array_push($poles[$ptr2], $top);
}
 
function dispPoles(){ 
    global $poles;
    echo "A: [".implode(", ", $poles[0])."] ";
    echo "B: [".implode(", ", $poles[1])."] ";
    echo "C: [".implode(", ", $poles[2])."] ";
    echo "\n\n";
}
 
$numdisks = 4;
initPoles($numdisks);
echo "Tower of Hanoi Solution for $numdisks disks: \n\n";
dispPoles();
TOH($numdisks);
```
## Javascript
```js
<script>
// javascript recursive function to
// solve tower of hanoi puzzle
function towerOfHanoi(n, from_rod,  to_rod,  aux_rod)
{
        if (n == 0)
        {
            return;
        }
        towerOfHanoi(n - 1, from_rod, aux_rod, to_rod);
        document.write("Move disk " + n + " from rod " + from_rod +
        " to rod " + to_rod+"<br/>");
        towerOfHanoi(n - 1, aux_rod, to_rod, from_rod);
    }
 
    // Driver code
    var n = 4; // Number of disks
    towerOfHanoi(n, 'A', 'C', 'B'); // A, B and C are names of rods
 
// This code is contributed by gauravrajput1
</script>
```
# Recursion Learn here

# [Click here](https://github.com/Subham-Maity/java-recursion-and-backtracking)