# F401_FMS_FCX10_LED_REVERSE

STM32F401CCU6 Blackpill

STM32 F4 FW 1.28.1

STM32CubeIDE v1.16.0

HAL

This code was written to drive the internal LED driver of the FMS FCX10 model vehicle. The signals were measured directly from the vehicle with a logic analyzer.

For each element in the `fms_led` array, "0" means `Deactive`, "1" means `Active`.

The state of each element in the array is sent for 3ms.

If the element in the array is 0, the square wave is high for 1ms and then low for 2ms.

If the element in the array is 1, the square wave is high for 2ms and then low for 1ms.

The 9th element should always be 0 and then low for 3ms. 

The total signal duration is 30ms(~33.3Hz) and send periodically.

Enhanced coding may be required to dynamically change the elements within the array at runtime.

 ```  
int fms_led[9] = { // 1: HIGH, 0: LOW
		0, // right signal
		0, // left signal
		0, // ILL 1.step
		0, // ILL 2.step
		0, // ? probably unused/free pin on the led driver
		0, // reverse/brake
		1, // no signal fast blink (low prio)
		1, // no signal slow blink (high prio)
		0  // always must be LOW
};
 ```  
LED Driver is FLYSKY FS-DB01.

3in1 ESC (ESC+Receiver+LED Drive Signal) is [FS-R11D-ESC-BS](https://www.flysky-cn.com/fsr11descbsspecification).

Transmitter is [FS-MG11-BS](https://www.flysky-cn.com/fsg4pbsspecification-copy).

# CubeMX configs:
![alt text](https://github.com/osos11-Git/F401_FMS_FCX10_LED_REVERSE/blob/main/pics/cubemx_pin.png)

![alt text](https://github.com/osos11-Git/F401_FMS_FCX10_LED_REVERSE/blob/main/pics/cubemx_config.png)

# Default Signal (No Connection, Transmitter Off, Slow Blink Mode):
![alt text](https://github.com/osos11-Git/F401_FMS_FCX10_LED_REVERSE/blob/main/pics/default_no_connection.png)
![alt text](https://github.com/osos11-Git/F401_FMS_FCX10_LED_REVERSE/blob/main/pics/blink.png)
![alt text](https://github.com/osos11-Git/F401_FMS_FCX10_LED_REVERSE/blob/main/pics/last_edge.png)

# Left Signal (Connected, Transmitter On):
![alt text](https://github.com/osos11-Git/F401_FMS_FCX10_LED_REVERSE/blob/main/pics/left_Signal.png)



