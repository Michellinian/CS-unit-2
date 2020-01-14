Homeworks
========


### 0. Revisiting For Loop functions 

This section is the introduction task to arduino. We did a for loop program when learning bash in the previous unit, and in this task, to familiarize with the new programming language (i.e. syntax), we did an introductory course, which was to recreate the for loop task that we did in bash, in arduino. We created the exact same function but using a different programming language. The tasks were: 

⓪ Create a program that prints 1000 times a greeting from your language. E.g: Hola, Hola, Hola,...

① Create a program that prints the years from 1000 to 2019 with the word year attached. E.g: Year 1000, Year 1001,...

② Create a program that prints all the odd numbers from 1001 to 1 (reversed).

③ Create a program that prints the addition of all the odd numbers, and all the even numbers from 1 to 1000.

④ Create a program that prints 100 factors of the number 7. E.g. 7, 14, 21, ...

⑤ Create a program that prints 1000 numbers in the sequence 012345601234560...

⑥ Create a program that prints the ordinal numbers from 1st to 100th, with the proper ending (st, nd, th). E.g: 1st, 2nd, 3rd, ...

By using tinkercad, which is an online software, where you can use it to write the code and run it in a virtual circuit to check if the code is meeting its expectations. These are codes that I came up with:

```sh 
#Program 0: prints out 1000 hellos
void setup()
{
  Serial.begin(9600);
  for (int count=0; count<1000; count++) {
    Serial.println("Hello");
  }
}

#Program 1: prints out years from 1000 to 2019  
void setup()
{
  Serial.begin(9600);
  for (int count=1000; count<=2019; count++) {
    Serial.print ("Year ");
    Serial.println (count);
  }
}

#Program 2: counts down the odd numbers form 1001 to 1
void setup()
{
  Serial.begin(9600);
  for (int count=1001; count>=1; count=count-2)
  {
    Serial.println (count);
  }
}
 
#Program 3: Calculate the sum of each, odd and even numbers from 1 to 100
void setup()
{
  Serial.begin(9600);
  float odd = 0;
  float even = 0;
  
  for (int a=0; a<=1000; a+=2)
  {
    even+=a;
  }
  
  for (int b=1; b<1000; b+=2)
  {
    odd+=b;
  }
  
  Serial.println(even);
  Serial.println(odd);
}


#Program 4: Prints 100 factors of 7
void setup()
{
  Serial.begin(9600);
  int num = 7;
  for (int count=1; count<100; count++ ) 
  {
    num+=7;
    Serial.println(num);
  }
}
  

#Program 5: Prints out sequence 01234560123.. for 1000 times
void setup()
{
  Serial.begin(9600);
  
  int num = -1;
  for (int count=1; count<1000; count++) 
  {
    num++;
    Serial.println(num);
    if (num==6)
    {
      num = -1;
    }
  }
}

#Program 6: Count numbers using st, nd, rd, th... from 1st to 1000th 
void setup()
{
  Serial.begin(9600);
  for (int num=1; num<=100; num++)
  {
    if (num%10==1 && num!=11)
    {
      Serial.print(num);
      Serial.println ("st");
    }
    else if (num%10==2 && num!=12)
    {
      Serial.print(num);
      Serial.println ("nd");
    }
    else if (num%10==3 && num!=13)
    {
      Serial.print(num);
      Serial.println ("rd");
    }
    else 
    {
      Serial.print(num);
      Serial.println ("th");
    }
  }
}
```
I only copied the setup() function of the program, because the rest of the code is exactly the same in every program. I could've also put these codes in the loop() function, although I did't want the code to execute infinite time, and instead I needed the code to executed only once. This is why I wrote it in the setup function. 

Comparing with the bash program it is very similar. You can tell that the two codes commands the computer to do the exact same thing. Although there are some difference in the syntaxes. 

First of all in arduino `Serial.begin(9600)`, is required in the beginning to execute the code. If this is not included in the code, the code itself would still be executed, although the result would not be printed on the console. 

Also the command for printing things is different between bash and arduino. In bash it is `echo \(message)`, although in arduino it is `Serial.println(\(message))`. The command `println`, means print the message and then go to a new line. Thus, without the "ln", this would just print out message in one line, without going down to a new line. 

Furthermore, another difference is that, when declaring a variable we always need to indicate what type of variable is it (i.e. whether if it's an int, string, etc.). Without indicating the the variable type, the computer would get confused, and would return an error.

### 1.Traffic Light Program

This is the virtual circuit of the program:

![TrafficLightProgram](trafficLight.png)

The following is the actual code of this program:

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

