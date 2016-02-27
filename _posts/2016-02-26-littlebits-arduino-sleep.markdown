---
layout: post
title:  "Resetting littleBits Arduino"
date:   2016-02-26 10:42:15 -0500
---

# I bricked my Arduino
I grabbed the [Arduino Coding Kit](http://littlebits.cc/kits/arduino-coding-kit) (really an Arduino Leonardo) the other day.
I will post what I am building with it later, but long story short **I bricked it**.

> This is not a bash on littleBits, I think they're awesome (although a little pricy). 

# How to fix it 

Ok, so you messed up your littleBits arduino somehow, you need to restart it.

You will need:

1. Arduino board + USB cable
1. Power module 
1. Some sort of conductive cable (I used some soldering wick as my cable.)


In short, you need to __short circuit__ the board to restart it. 

1. Find the two middle holes on the `a2` and `d10` row. ![Holes](/assets/short_circuit.jpg)
1. Place the cable to connect those holes. ![connectedHoles](/assets/connection.jpg)
1. Connect USB cable to computer and arduino.
1. Turn ON your arduino board (via power module)
1. Launch Arduino IDE and have bug-free code ready
1. Start to Upload the code. When the status changes from `Compiling sketch` to `Uploading`, remove the short circuit.
1. You should see LED's flashing and the Arduino should be reset.


# More about the problem

I've done some research as to why this happens. I think it boils to a couple things:

1. Either you uploaded larger files than its memory can handle
1. Or you used a library that messes up the firmware on the board.

I personally used [JeeLib](https://github.com/jcw/jeelib), a library designed to help with power consumption on the
boards. I'm assuming that messed up some LED controllers that ended up messing up the entire system.
