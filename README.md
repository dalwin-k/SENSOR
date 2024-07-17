# Water-Level-Sensor-With-Arduino

How does a Water Level Sensor Work and How to Interface it with Arduino? 

![image](https://github.com/user-attachments/assets/dc53a588-9df8-41f8-9172-a36fb97a410f)


COMPONENTS: Sensors: Conducting Plates Actuators 

(Output Devices): LED (connected to pin D6) 

Active Electronic Components: NPN Transistor 

Passive Electronic Components: Resistor (Emitter Resistor) 

Power Supply Components: 5V Supply Voltage 

Microcontroller Board: Arduino Board

ROBODO REL_35 WATER LEVEL DEPTH SENSOR:

Operating Voltage: DC 3-5V

Operating Current: Less than 20mA

Sensor Type: Analog

Detection Area: 40mm x 16mm

Production Process: FR4 double-sided

Operating Temperature: 10°C - 30°C

Humidity: 10% - 90% non-condensing

Product Dimensions: 60mm x 20mm



Type of Sensor:

The RoboDo REL_35 is an analog water level depth sensor, meaning it provides an analog output signal
proportional to the water level or depth.

Operating Principle:

The specific operating principle of the sensor may vary, but water level sensors generally use methods
like resistive or capacitive sensing. Without the exact technical documentation for REL_35, it's essential
to refer to the manufacturer's datasheet for precise information.

Measuring Range:

The REL_35 is designed to measure water levels within a certain depth range. The range is typically
specified by the manufacturer and is important for understanding the sensor's suitability for different
applications.

Output Signal:

Being an analog sensor, REL_35 likely provides an analog voltage or current signal corresponding to the
water level. The output signal varies based on the depth of the water.

Connection Interface:

The sensor is likely to have a connection interface for integration with microcontrollers like Arduino. In
your provided Arduino code, A0 is specified as the analog input pin, indicating compatibility with sensors
like REL_35.

Calibration and Thresholds:

Water level sensors often require calibration to convert raw sensor readings into meaningful depth
measurements. The code you provided has a threshold (540) to filter out low sensor readings.

Application:

Water level sensors find applications in various fields such as environmental monitoring, agriculture,
industrial processes, and home automation. They are useful for monitoring water levels in tanks, rivers,
or other water bodies.

Accuracy and Precision:

The accuracy and precision of the REL_35 depend on the sensor's design and specifications. The
datasheet would provide details on factors such as resolution and accuracy.

Datasheet:

For comprehensive technical details, it is crucial to refer to the manufacturer's datasheet for the REL_35
sensor. The datasheet typically includes specifications, electrical characteristics, and usage guidelines.

WORKING:

Sensor Type:

Water level sensors come in various types, including resistive, capacitive, and ultrasonic sensors. The
RoboDo REL_35 is specified as an analog sensor, so it likely operates based on changes in resistance or
capacitance.

Detecion Area:

The specified detection area (40mm x 16mm) indicates the part of the sensor that interacts with the
water. This area is crucial for accurate readings, and the sensor's response may vary based on the surface
it's in contact with.

Electrical Properties:

Analog water level sensors often rely on changes in electrical properties. For resistive sensors, the
resistance between two points changes based on the water level. For capacitive sensors, the capacitance
between electrodes changes.

Voltage and Current:

The specified operating voltage (DC 3-5V) and operating current (less than 20mA) indicate the electrical
requirements for the sensor. Applying the correct voltage ensures reliable sensor operation.

Production Process:

The fact that it's manufactured using FR4 double-sided suggests a durable and standard PCB (Printed
Circuit Board) material, which is common in electronic components.

Temperature and Humidity:

The specified operating temperature (10°C - 30°C) and humidity (10% - 90% non-condensing) provide
environmental constraints. Operating within these limits ensures accurate and reliable readings.
Sensor Operation in Water Level Monitoring System (Arduino Code):

Initialization:

The Arduino code initializes serial communication and sets up the pins (e.g., A0 for analog input, D6 for
LED output).

Reading Sensor Value:

In the loop, the code reads the analog value from the water level sensor using analogRead(sensorPin).

Threshold Check:

It checks if the sensor value is below a specified threshold (540). This serves as a minimum reading to
filter out false values when the sensor is not submerged.

Mapping Values:

The sensor values are then mapped using the map() function. This maps the raw sensor values from the
specified detection range to a range suitable for controlling LED brightness (0-255).

Output to Serial Monitor:

The raw sensor value and the mapped output value are printed to the serial monitor for monitoring and
debugging purposes.

LED Control:

The mapped output value is used to control the LED brightness using analogWrite(ledPin, outputValue).

Overall Process:

The water level sensor, when submerged, exhibits changes in its electrical properties. The Arduino reads
these changes, applies thresholds and mappings, and then uses the information to control an output
device (LED) to visually represent the water level. This process is repeated continuously in the loop,
allowing real-time monitoring of water levels.

![image](https://github.com/user-attachments/assets/2ceab915-5c6e-4968-b819-1d2205425240)


CODE EXPLAINED:

// Sensor pins pin D6 LED output, pin A0 analog Input

#define ledPin 6

#define sensorPin A0

void setup()

{

Serial.begin(9600); // Initialize serial communication at 9600 baud rate

pinMode(ledPin, OUTPUT); // Set the LED pin as an output

digitalWrite(ledPin, LOW); // Turn off the LED initially

}

void loop()

{

unsigned int sensorValue = analogRead(sensorPin); // Read the analog value from the sensor

if (sensorValue < 540)

return; // If the sensor value is below 540, exit the loop

uint8_t outputValue = map(sensorValue, 540, 800, 0, 255); // Map the sensor value from the range

540-800 to the range 0-255

Serial.print(sensorValue); // Print the raw sensor value

Serial.print(" ");

Serial.println(outputValue); // Print the mapped output value

analogWrite(ledPin, outputValue); // Generate a PWM signal to control the LED brightness


}

