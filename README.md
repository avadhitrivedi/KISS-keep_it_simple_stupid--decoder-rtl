# KISS-keep_it_simple_stupid--decoder-rtl
KISS (Keep It Simple Stupid) is a byte-oriented framing protocol commonly used in telemetry, telecommand, and serial communication systems.
A KISS decoder converts an incoming framed byte stream into raw payload data.

The KISS decoder receives an 8-bit input data stream along with a valid signal. 
1. Consider the raw payload size as 256 bytes 
2. Detect the start and end of a frame 
3. Decode escaped special characters 
4. Output only the raw payload bytes 
5. Indicate the start and end of each decoded frame using pulse signals 
The entire design is fully synchronous to a single system clock. 

Protocol Rules: 
1. Every frame starts and ends with FEND (0xC0). 
2. If the payload contains FEND, it is transmitted as FESC TFEND. 
3. If the payload contains FESC, it is transmitted as FESC TFESC.

1. Raw payload size=256 bytes 
2. Payload size might become more than 256 bytes after KISS encoding 
3. After KISS decoding, it should be 256 bytes
   
