# Calculator
Introduction: 
The purpose of this project was to create a cohesion between our theoretical and practical knowledge from our course EEE 4307 (Digital Electronics). Skillsets from the software and hardware labs were merged and utilized to create a basic calculator with addition, subtraction, division and multiplication features. 
Designs were using breadboard and finally put it on a printed circuit board (PCB). The final output is displayed using 7-segment displays. The ICs were placed on the PCB and soldered. 

Problem Formulation:  
The main objective of this project was to design a functional calculator with addition, subtraction, multiplication and division operation. And display the results using a 7-segment display. This bridges all the knowledge gained from our theoretical course and labs and application to real world problems. Initially, addition, subtraction, multiplication and division circuits were designed in Proteus software using combinational logic. Then, design was modeled on breadboards using ICs and jumpers. 
ICs, breadboard, jumpers, multimeter, soldering iron and other accessories were bought from electronic shops. The detailed expenditure list has been attached with the report later on. Then PCB was soldered with the ICS accordingly. The details of which are discussed below. 
 
Designing Procedure: 
For designing the circuit, combinational logic was used using logic gates and desired outputs were found using the characteristics of XOR, OR, AND, NOT and Full Adder ICs. When outputs were achieved on paper, software simulation was completed using Proteus 8 software. The design was checked for different inputs. After obtaining desired output PCB layout was designed. 
While designing PCB all the ICs were first placed. In design rule manager, signal line was set to T30 and Power line to T40. Bottom copper was used horizontally and top copper vertically followed by auto routing to make the connections. There were some CRC errors which were corrected by moving the connecting coppers manually. But there were no DRC errors. Although a lot of copper connections didn’t require to connect, there were a lots of vias. The number of these vias could be lessened if the top and bottom copper were connected manually.

Adder and Subtractor Designing: 
Adder and subtractor were designed using the combinational logic we learned in our theory course. First, a schematic of the circuit was made using the required logic gates in Proteus 8 software. Then, results were verified.
Then, the PCB layout was made using the designing procedure outlined above. Then, a checker circuit was also designed for the adder operation. This checker gave outputs for two 7-segment displays if the summation was greater than 9 by adding 6 to the output. The details are given in the K-Map attached. 
A selection bit was added which allows to select either addition or subtraction. If the selection bit=0, the circuit performs addition, if selection bit=1, the circuit performs subtraction operation. 
The results are displayed using 7-segment display, which is placed on a breadboard.
The input numbers are in binary form. Breadboard was used to place inputs from the power source. 

Fuller Adder (74LS283)= 2,
XOR (74HC86)= 2,
AND (7408)= 2,
NOT (7404) = 1,
OR (7432)= 1,
Therefore, total number of ICs= 8.

Multiplier Designing: 
Multiplier was divided into two parts:
1.	Binary Adder
2.	Binary to BCD converter
Binary adder was designed with simple multiplication rule, in which every digit was put into AND gate with other. Then the results were added accordingly with full adders. This gave a 7 bit binary number. To convert that 7 bit binary number, Binary to BCD logic circuit was used. This converter was made base on shift add 3 method. That is if any part of the binary number was found >4,(0I00) 3(00II) was added and each time a shift of digit from MSB to LSB was made.
To make the checker circuit to check if binary number is greater than 4, a checker was designed using online K-MAP generator. After each checker a binary full adder was there of which input A was the binary number and input B was 3 (00II).
As binary number was 7 digit, adding one extra checker and one extra 3 (00II) adder was needed. Logic diagram is given below as a screenshot of the pdf page.
After getting all the results the 7 binary numbers were put through 2 different 7 segment display.
IC used:
For binary multiplicator part:
4 7408 (AND) IC
3 74ls283 (Binary Full Adder) IC
For Converter part:
4 74ls283 (Binary Full Adder) IC
2  7408 (And) IC
2 7432(OR) IC

Divider Designing:
The approach that was made to solve divider circuit is subtracting the divider from the dividend. Depending on how many times a Divider can be subtracted from the dividend (until negative output occurs) the result is that number of times.
Like if dividing 9 by 3, 3 can be subtracted 3 times from 9. Further subtraction will result in negative number, so result is 3.
So in this logic design I basically used subtractor circuit again and again and added the number of subtractor circuit that was needed before carry out bit of any of the subtractor gives 0, (that means subtraction result is negative).
But to do this maximum number of 9 subtractor circuit ( for dividing with 1) is needed.
That would make the PCB too big. So a modification of used here. Instead of subtracting 1, the lowest number that was allowed to subtract was 2. That makes requirement of only 4 subtractor circuit maximum.  (As the highest number of subtraction would occur in dividing 9 by 2, requires 4 subtractor circuit )
While dividing with 1 my goal was to make the dividend (A input) the output (result) of the logic circuit. So whenever 1 comes as the dividend, the input A was made to crossover and overlap the regular output.

Drawback:
This circuit doesn’t show any error while dividing a number with 0. It gives an output of a random number which is wrong. So in my logic design user will get an output if he divides something with 0 which is not possible.
IC used:
For each subtractor circuit:
1 7486 (XOR) IC
1 74ls283 (Binary full adder) IC
1 7408 (And gate)
Total IC used 14.
 

Simulation Results:
(Attached as Proteus files) 
