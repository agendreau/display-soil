# Sound Sensor Data Display

## Introduction
When you press ``||input: button A||``, turn on ``||Neopixel: yellow lights||`` ``||logic: if||`` the ``||gatorSoil: soil moisture||`` is ``||logic: less||`` than 5  and ``||Neopixel: green lights||`` if the ``||gatorSoil: soil moisture||`` is ``||logic: more than||`` 5. Things to think about. Which pin controls the Lights on the gator:bit? How mand LEDs are on the gator:bit? Draw a picture to help think about the logic.

## Step 1
``||basic: Initialize||`` the LEDs to that ``||variables: strip||`` can control them.

```blocks
let strip = neopixel.create(DigitalPin.P12, 5, NeoPixelMode.RGB)
```

## Step 2 
Code your micro:bit to take a sound reading when ``||input: button A||`` is pressed. Set the ``||neopixel: brightness||`` of the strip to 50, so the lights are not extremely bright.

```blocks
let strip = neopixel.create(DigitalPin.P12, 5, NeoPixelMode.RGB)
input.onButtonPressed(Button.A, function () {
    strip.setBrightness(50)
})
```

## Step 3
Now code your micro:bit to display ``||Neopixel: yellow lights||`` when  ``||gatorSoil: soil moisture||`` 
is ``||logic: less than||`` 5.

```blocks
let strip = neopixel.create(DigitalPin.P12, 5, NeoPixelMode.RGB)
input.onButtonPressed(Button.A, function () {
        strip.setBrightness(50)
        if (Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10) < 5) {
            strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
        } 
})
```

## Step 4
Now code your micro:bit to display ``||Neopixel: green lights||`` when  ``||gatorSoil: soil moisture||`` 
is ``||logic: greater than||`` 5 decibles.  


```blocks
let strip = neopixel.create(DigitalPin.P12, 5, NeoPixelMode.RGB)

input.onButtonPressed(Button.A, function () {
        strip.setBrightness(50)
        if (Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10) < 5) {
            strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
        } else {
            strip.showColor(neopixel.colors(NeoPixelColors.Green))
        }
})
```
## Step 5
``|Download your code|`` and try it out

## Step 6
Modify the program so that when you press ``||input: button B||``, 
if the ``||gatorSoil: soil moisture||`` is less than 5, 
the gator:bit ``||music: plays a song||``. 

```blocks
input.onButtonPressed(Button.B, function () {
    if (Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10) < 5) {
        music.beginMelody(music.builtInMelody(Melodies.Ode), MelodyOptions.Once)
    }
})
```

## Step 7
``|Download|`` your code and try it out

## Step 8
Modify either the lights or music to ``||Loops: repeat||`` 5 times

```blocks
input.onButtonPressed(Button.A, function () {
    for (let i = 0; i < 5; i++) {
        strip.setBrightness(50)
        if (Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10) < 5) {
            strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
        } else {
            strip.showColor(neopixel.colors(NeoPixelColors.Green))
        }
    }
})
```

## Step 9
``||basic: wait||`` 10 seconds in between each time the sensor takes a reading

```blocks
input.onButtonPressed(Button.A, function () {
    for (let i = 0; i < 5; i++) {
        strip.setBrightness(50)
        if (Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10) < 5) {
            strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
        } else {
            strip.showColor(neopixel.colors(NeoPixelColors.Green))
        }
        basic.pause(10000)
    }
})
```
## Step 10
``|Download|`` the code and try it out.


```package
gatorSoil=github:sparkfun/pxt-gator-soil
neopixel=github:microsoft/pxt-neopixel
```





