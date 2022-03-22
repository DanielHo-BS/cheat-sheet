# Introduction
Libmraa is a C/C++ library with bindings to Python, Javascript and Java to interface with the I/O on Galileo, Edison & other platforms, with a structured and sane API where port names/numbering matches the board that you are on. Use of libmraa does not tie you to specific hardware with board detection done at runtime you can create portable code that will work across the supported platforms.

The intent is to make it easier for developers and sensor manufacturers to map their sensors & actuators on top of supported hardware and to allow control of low level communication protocol by high level languages & constructs.

# [doc](http://iotdk.intel.com/docs/master/mraa/python/index.html)

# API
* Aio
* I2c
* Gpio
* Led
* Pwm
* Spi
* Uart
* Common