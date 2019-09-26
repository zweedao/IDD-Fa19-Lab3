# Data Logger (and using cool sensors!)

*A lab report by Zwee Dao.*

## In The Report

Include your responses to the bold questions on your own fork of [this lab report template](https://github.com/FAR-Lab/IDD-Fa18-Lab2). Include snippets of code that explain what you did. Deliverables are due next Tuesday. Post your lab reports as README.md pages on your GitHub, and post a link to that on your main class hub page.

For this lab, we will be experimenting with a variety of sensors, sending the data to the Arduino serial monitor, writing data to the EEPROM of the Arduino, and then playing the data back.

## Part A.  Writing to the Serial Monitor
 
**a. Based on the readings from the serial monitor, what is the range of the analog values being read?**
0 - 1023
 
**b. How many bits of resolution does the analog to digital converter (ADC) on the Arduino have?**
10 bits

## Part B. RGB LED

**How might you use this with only the parts in your kit? Show us your solution.**
Just simply connect the 4 legs of RGB LED with proper ports. 
[RGB led video](/rgb_led.MOV)

## Part C. Voltage Varying Sensors  
### 1. FSR, Flex Sensor, Photo cell, Softpot

**a. What voltage values do you see from your force sensor?**
4.5V

**b. What kind of relationship does the voltage have as a function of the force applied? (e.g., linear?)**
The graph looks kind of linear. The more force I apply, the more voltage value.

**c. Can you change the LED fading code values so that you get the full range of output voltages from the LED when using your FSR?**
I normalize the FSR values to be in the same range as LED values: `brightness = analogRead(A0)\*255/1024;`
[FSR controlling LED video](/fsr_led.MOV)

<pre><code>
int led = 9;           // the PWM pin the LED is attached to
int brightness = 0;    // how bright the LED is
int fadeAmount = 5;    // how many points to fade the LED by


void setup() {
  // declare pin 9 to be an output:
  pinMode(led, OUTPUT);
  
  // initialize the serial communication:
  Serial.begin(9600);
}

void loop() {
  Serial.println(analogRead(A0));
  
  // change the brightness for next time through the loop:
  brightness = analogRead(A0)\*255/1024;
  analogWrite(led, brightness);
  delay(30);
}
</code></pre>

**d. What resistance do you need to have in series to get a reasonable range of voltages from each sensor?**


**e. What kind of relationship does the resistance have as a function of stimulus? (e.g., linear?)**


### 2. Accelerometer
 
**a. Include your accelerometer read-out code in your write-up.**

### 3. IR Proximity Sensor

**a. Describe the voltage change over the sensing range of the sensor. A sketch of voltage vs. distance would work also. Does it match up with what you expect from the datasheet?**

**b. Upload your merged code to your lab report repository and link to it here.**

## Optional. Graphic Display

**Take a picture of your screen working insert it here!**

## Part D. Logging values to the EEPROM and reading them back
 
### 1. Reading and writing values to the Arduino EEPROM

**a. Does it matter what actions are assigned to which state? Why?**

**b. Why is the code here all in the setup() functions and not in the loop() functions?**

**c. How many byte-sized data samples can you store on the Atmega328?**

**d. How would you get analog data from the Arduino analog pins to be byte-sized? How about analog data from the I2C devices?**

**e. Alternately, how would we store the data if it were bigger than a byte? (hint: take a look at the [EEPROMPut](https://www.arduino.cc/en/Reference/EEPROMPut) example)**

**Upload your modified code that takes in analog values from your sensors and prints them back out to the Arduino Serial Monitor.**

### 2. Design your logger
 
**a. Insert here a copy of your final state diagram.**

### 3. Create your data logger!
 
**a. Record and upload a short demo video of your logger in action.**
