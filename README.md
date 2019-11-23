Martian Decoder
-----------

Contents
========

1. PLanning 
2. Design 
3. Development 
4. Evaulation 


Planning
======

### Binary Code
**How does binary number work?**

| A | B | C | D |             
| ---| --- | --- | --- |     
| 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 0 |
| 1 | 1 | 1 | 1 |

This is the table of the binary numbers from 0 to 16. From this table we observe how each digit have their own distinct pattern. In D, 0 and 1 change one by one. In other words, the pattern "01" is repeated through the whole table as you go down. In C, the pattern becomes "0011", and in B it is "00001111", and finally in A it is "0000000011111111". What is happening here is that 0 and 1 are forming some kind of pattern that are repeated as the number becomes bigger and bigger. In d, 0 and 1 are changing one by one, which gives us the total "sequence segment" number of 2. After one "01", then comes another "01". In C, it is "0011", that is repeated and the total number of 0 and 1 in this pattern is. Then in B it is 8, and in A it is 16. We can see how the number increases by the number of exponents of 2, meaning 2, 4, 8, 16,.... 

### Binary Gates
**What are binary gates?**

Design
======

Development
========

### 1.Traffic Light Program**

This is the virtual circuit of the program:


```sh 
// assigning integer for each leds (same number as the arduino input)
int redLight = 13; 
int yellowLight = 12;
int greenLight = 11;

void setup() {
  // the code would only run once
  // setup of which sources are the input and output
  pinMode(redLight, OUTPUT);
  pinMode(yellowLight, OUTPUT);
  pinMode(greenLight, OUTPUT); 
}

void loop() {
  // the code would run repeatedly
  // Calling out the function below, by assigning the arguments
  blinkColor(1000, redLight);
  blinkColor(1000, yellowLight);
  blinkColor(1000, greenLight);
}

// Parameters to reuse them
void blinkColor(int t, int color) {
  // parameters specified in the above loop function
  digitalWrite(color, HIGH);
  delay(t);
  digitalWrite(color, LOW);
  delay(t);
}
```

This code simply turns on the red led first, and then after 1 second, it turns on yellow light, and turn off the red, then after another second, does the same process but with green color. By calling out the blinkColor in the loop function, it runs infinitely until we stop the simulation. By using parameters in the blinkColor function, we can set different arguments in the same fucntion, in other words, reuse the same function but for another purpose. HIGH, means turn on, and LOW means turn off in arduino, and this appears a lot so it is better if we remember this.


### Binary lights

This program should light the leds in 15 different ways by using the binary numbers.
Steps: 
1. Create 4 leds (Each representing the digits of binary numbers)
2. Create a for loop that counts until 15 
3. For each count convert decimal to binary using module(%)
4. If statements to assign when count%x is y then light the designated leds

```sh 
// Assiging the input numbers in the arudino board
int redLight = 13;
int blueLight = 12;
int yellowLight = 11;
int whiteLight = 10;

void setup() {
  pinMode(13, OUTPUT);
  pinMode(12, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(10, OUTPUT);
}

void loop() {
  // Calling the function 
  countBinary();
}

void countBinary() {
  for (int count=0; count<=15; count++) {
    //led D
    if (count%2 == 1) {
      digitalWrite(whiteLight, HIGH);
    } else {
      digitalWrite(whiteLight, LOW);
    }
    //led C
    if (count%4 > 1) {
      digitalWrite(yellowLight, HIGH);
    } else {
      digitalWrite(yellowLight, LOW);
    }
    //led B
    if (count%8 > 3) {
      digitalWrite(blueLight, HIGH); 
    } else {
      digitalWrite(blueLight, LOW);
    }
    //led A
    if (count%16 > 7) {
      digitalWrite(redLight, HIGH);
    } else {
      digitalWrite(redLight, LOW);
    }
    delay(1000);
  }
  
}
```
The outcome is that the 4 lights represent each digit in hte binary numbers, and that when the digit number is 1, then it turns on the light, when it is 0 then otherwise. In this program this is what is happening:

| Decimal | digit C | decimal%4 |
| --- | --- | --- |
| 1 | 0 | 0 |
| 2 | 0 | 1 |
| 3 | 1 | 2 | 
| 4 | 1 | 3 |
| 5 | 0 | 0 |
| 6 | 0 | 1 |
| 7 | 1 | 2 |

In this table we can see, how when the decimal%4 becomes bigger than 1, then C is 1. Therefore the code: 
```sh 
if (count%4 > 1) {
  digitalWrite(yellowLight, HIGH);
}
```
since the 1 means HIGH. The code works like this, and by representing each leds as digits A, B, C, D of binary numbers, we can light the 4 leds in 15 different ways, using the concept of binary numbers.

### Development of Weekend Task

**Table 1:**

| butA | butB | out1 | out2 |
| --- | --- | --- | --- |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |

Step: 
1. Create variable for all inputs and outputs
2. Create if statements saying "if these inputs are on, and turn on these inputs"

```sh 
int butA = 13;
int butB = 12;
int out1 = 3;
int out2 = 4;

void setup() {
  pinMode(butA, INPUT);
  pinMode(butB, INPUT);
  pinMode(out1, OUTPUT);
  pinMode(out2, OUTPUT);
}

void loop() {
  if (digitalRead(butA)==LOW && digitalRead(butB)==LOW) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, LOW);
  } else if (digitalRead(butA)==LOW && digitalRead(butB)==HIGH) {
    digitalWrite(out1, LOW);
    digitalWrite(out2, HIGH);
  } else if {digitalRead(butA)==HIGH && digitalRead(butB)==LOW) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, HIGH);
   } else if (digitalRead(butA)==HIGH && digitalRead(butB)==HIGH) {
    digitalWrite(out1, LOW);
    digitalWrite(out2, LOW);
  }
}
```
This code is using conditional statements to decide on which output is HIGH and LOW, depending on which input is HIGH and LOW. 

**Table 2:**


| butA | butB | out1 | out2 |
| --- | --- | --- | --- |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 |

The condition slightly changes, although the whole structure of the code is exactly the same. 
```sh 
int butA = 13;
int butB = 12;
int out1 = 3;
int out2 = 4;

void setup() {
  pinMode(butA, INPUT);
  pinMode(butB, INPUT);
  pinMode(out1, OUTPUT);
  pinMode(out2, OUTPUT);
}

void loop() {
  if (digitalRead(butA)==LOW && digitalRead(butB)==LOW) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, LOW);
  } else if (digitalRead(butA)==LOW && digitalRead(butB)==HIGH) {
    digitalWrite(out1, LOW);
    digitalWrite(out2, HIGH);
  } else if {digitalRead(butA)==HIGH && digitalRead(butB)==LOW) {
    digitalWrite(out1, LOW);
    digitalWrite(out2, HIGH);
   } else if (digitalRead(butA)==HIGH && digitalRead(butB)==HIGH) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, HIGH);
  }
}
```

**Table 3**


| butA | butB | but C | out1 | out2 |
| --- | --- | --- | --- | --- | 
| 0 | 0 | 0 | 1 | 1 | 
| 0 | 0 | 1 | 1 | 1 | 
| 0 | 1 | 0 | 1 | 0 | 
| 0 | 1 | 1 | 1 | 0 | 
| 1 | 0 | 0 | 0 | 1 | 
| 1 | 0 | 1 | 1 | 1 | 
| 1 | 1 | 0 | 1 | 1 | 
| 1 | 1 | 1 | 1 | 1 | 

This table is different from the last 2 tables, but the only difference is that there is one more input. Therefore there are more combinations of the buttons, and this mean that there will be more if statements in the code, although the structure is the same again, even for table 3.

```sh 
int butA = 13;
int butB = 12;
int butC = 11;
int out1 = 3;
int out2 = 4;

void setup() {
  pinMode(butA, INPUT);
  pinMode(butB, INPUT);
  pinMode(butC, INPUT);
  pinMode(out1, OUTPUT);
  pinMode(out2, OUTPUT);
}

void loop() {
  if (digitalRead(butA)==LOW && digitalRead(butB)==LOW && digitalRead(butC)==LOW) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, HIGH);
  } else if (digitalRead(butA)==LOW && digitalRead(butB)==LOW && digitalRead(butC)==HIGH) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, HIGH);
  } else if (digitalRead(butA)==LOW && digitalRead(butB)==HIGH && digitalRead(butC)==LOW) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, LOW);
  } else if (digitalRead(butA)==LOW && digitalRead(butB)==HIGH && digitalRead(butC)==HIGH) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, LOW);
  } else if (digitalRead(butA)==HIGH && digitalRead(butB)==LOW && digitalRead(butC)==LOW) {
    digitalWrite(out1, LOW);
    digitalWrite(out2, HIGH);
  } else if (digitalRead(butA)==HIGH && digitalRead(butB)==LOW && digitalRead(butC)==HIGH) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, HIGH);
  } else if (digitalRead(butA)==HIGH && digitalRead(butB)==HIGH && digitalRead(butC)==LOW) {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, HIGH);
  } else {
    digitalWrite(out1, HIGH);
    digitalWrite(out2, HIGH);
  }
}
```

In this program the code becomes very long, but essentially we are doing the same thing in table 1 and 2, but with a lnger process, since there is one more input to consider.

### 4. Using Binary Gates for Weekend Task
**Table 1**

Using the same table as before, we are going to another code that performs exactly the same thing, but with a different method. By using binary gates. This is table for the first output.

| b\a | 0 | 1 |
| --- | --- | --- |
| 0 | 1 | 1 |
| 1 | 0 | 0 | 

What we can observe here is that, the light turns on (becomes 1) when the button a and b are both 0 and, when button a is 1 and b is 0. These are the 2 scenarios that the led out1 turns on. Therefore, by using the concept of binary gates, we can come up with the equation `NOT B`. When "Not B", out1 turns on. Now that we sorted out out1, we also need to think about out2. 

| b\a | 0 | 1 |
| --- | --- | --- |
| 0 | 0 | 1 |
| 1 | 1 | 0 |

This is the table for out2. The equation for when the out2 turns on is `(NOT A) AND B OR A AND (NOT B)`. Therefore, the  previous code can be modified as in the following: 

```sh 
int butA = 13;
int butB = 12;
int out1 = 3;
int out2 = 4;

void setup() {
  pinMode(butA, INPUT);
  pinMode(butB, INPUT);
  pinMode(out1, OUTPUT);
  pinMode(out2, OUTPUT);
}

void loop() {
  bool A = digitalRead(butA);
  bool B = digitalRead(butB);
  
  bool eq1 = !B;
  bool eq2 = !A & B | !B & A;
  
  digitalWrite(out1, eq1);
  digitalWrite(out2, eq2);
}
```

By using binary gates the code becomes a lot more concise, and still it does the exact same thing. 

**Table2**
This is essentially the same step: 
1. Create a table for both out1 and out2
2. Then come up with equations for each output using binary gates
Firstly, this is the table for out1:

| b\a | 0 | 1 |
| --- | --- | --- |
| 0 | 1 | 0 |
| 1 | 0 | 1 |

Then by looking at the table, we can find the equation for when out1 turn on. In this case it is
`(NOT A AND NOT B) OR (A AND B)`. For the out2, this is the table: 

| b\a | 0 | 1 |
| --- | --- | --- |
| 0 | 0 | 1 |
| 1 | 1 | 1 |

In this other case, we can come up with the equation `A OR B`. Using these tables and binary gates equations, we can come with the following code: 
```sh 
int butA = 13;
int butB = 12;
int out1 = 3;
int out2 = 4;

void setup() {
  pinMode(butA, INPUT);
  pinMode(butB, INPUT);
  pinMode(out1, OUTPUT);
  pinMode(out2, OUTPUT);
}

void loop() {
  bool A = digitalRead(butA);
  bool B = digitalRead(butB);
  
  bool eq1 = !A & !B | A & B;
  bool eq2 = A | B;
  
  digitalWrite(out1, eq1);
  digitalWrite(out2, eq2);
}
```

This is the modified code. As mentioned before, it does the exact same performance.

**Table 3**
The same step is taken in this one, but with one more input. The table would be like this below.

Table for out1: 

| c\ab | 00 | 01 | 11 | 10 |
| --- | --- | --- | --- | --- |
| 0 | 1 | 1 | 1 | 0 |
| 1 | 1 | 1 | 1 | 1 | 

Table for out2: 

| c\ab | 00 | 01 | 11 | 10 |
| --- | --- | --- | --- | --- |
| 0 | 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 | 1 | 

Then we find the equation that best fits the conditions in the table, using bunary gates.

Equation for out1: `NOT A OR B OR C`

Equation for out2: `NOT A AND NOT B OR A`

This is code for table 3: 

```sh 
int butA = 13;
int butB = 12;
int butC = 11;
int out1 = 3;
int out2 = 4;

void setup() {
  pinMode(butA, INPUT);
  pinMode(butB, INPUT);
  pinMode(butC, INPUT);
  pinMode(out1, OUTPUT);
  pinMode(out2, OUTPUT);
}

void loop() {
  bool A = digitalRead(butA);
  bool B = digitalRead(butB);
  bool C = digitalRead(butC);
  
  bool eq1 = !A | B | C;
  bool eq2 = !A & !B | A;
  
  digitalWrite(out1, eq1);
  digitalWrite(out2, eq2);
}
```

This should essentially perform the same thing with the previous code, with long for loops. In conclusion, by using binary gates, it allows us to make the code more simple and line efficient. 














Evaluation 
=========

### Comparison of Bash & Arduino 

### 1. Bash
**Pros**

1. Less symbols (), {}, etc.
2. Very powerful
3. Quick execution speed
4. Great use for apple products / terminals
5. Easy to check errors

**Cons**

1. Very syntax specifc (single space mistake can lead to the code crashing)
2. No symbols result in confusion from time to time 
3. Syntax is very different from other programming language
4. Can only be used in terminal 

### 2. Arduino 
**Pros**

1. Alike with some other programming language 
2. Less space accuracy (even missing a space it still runs the code)
3. Can be used in a variety of platform 
4. Can use functions 

**Cons**
1. Sometimes hard to spot errors
2. Too many symbols (), {}, etc. 
3. Slow execution speed (simulation speed is way slower than bash)
4. Many different commands to remember



