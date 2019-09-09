# Sound Sensor Data Display

## Introduction
When you press ``||input: button A||``, ``||logic: if||`` the ``||gatorSoil: soil moisture||`` is ``||logic: less||`` than 60 then show a small heart ``||logic: else||`` show a bigh heart. Draw a picture to help think about what you want to happen. When you're ready click NEXT to start.

## Step 1
Code your micro:bit to take a a ``||gatotSoil: soil moisture||`` reading when ``||input: button A||`` is pressed and ``||basic: show||`` the results on the micro:bit. ``||Math: Multiply||`` the result by 100 to get the percentage moisture.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100)
})
```

## Step 3
Now code your micro:bit to display ``||basic: small heart||`` ``||logic: if||`` the  ``||gatorSoil: soil moisture||`` percentage 
is ``||logic: less than||`` 60. 

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100)
    if (gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100 < 60) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . # # # .
            . . # . .
            . . . . .
            `)
    }
})
```

## Step 3
Now code your micro:bit to display ``||basic: a big heart||`` if the ``||gatorSoil: soil moisture||`` 
is ``||logic: greater than||`` 60 percent.  


```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100)
    if (gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100 < 60) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . # # # .
            . . # . .
            . . . . .
            `)
    } else {
        basic.showIcon(IconNames.Heart)
    }
})
```
## Step 4
``|Download your code|`` and try it out

## Step 5
Modify the program so that when you press ``||input: button B||``, 
``||logic: if||`` the ``||gatorSoil: soil moisture||`` is ``||logic: less than||`` 50 percent, 
the gator:bit ``||music: plays a song||``. 

```blocks
input.onButtonPressed(Button.B, function () {
    if (gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100 < 50) {
        music.beginMelody(music.builtInMelody(Melodies.Ode), MelodyOptions.Once)
        basic.showString("WATER")
    }
})
```

## Step 6
``|Download|`` your code and try it out

## Step 7
Modify either the lights or music to ``||Loops: repeat||`` 5 times

```blocks
input.onButtonPressed(Button.A, function () {
    for (let i = 0; i < 5; i++) {
        basic.showNumber(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100)
        if (gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100 < 60) {
            basic.showLeds(`
                . . . . .
                . # . # .
                . # # # .
                . . # . .
                . . . . .
                `)
        } else {
            basic.showIcon(IconNames.Heart)
        }
    }
})
```

## Step 8
``||basic: wait||`` 10 seconds in between each time the sensor takes a reading

```blocks
input.onButtonPressed(Button.A, function () {
    for (let i = 0; i < 5; i++) {
        basic.showNumber(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100)
        if (gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1) * 100 < 60) {
            basic.showLeds(`
                . . . . .
                . # . # .
                . # # # .
                . . # . .
                . . . . .
                `)
        } else {
            basic.showIcon(IconNames.Heart)
        }
        basic.pause(10000)
    }
})
```
## Step 9
``|Download|`` the code and try it out.


```package
gatorSoil=github:sparkfun/pxt-gator-soil
neopixel=github:microsoft/pxt-neopixel
```





