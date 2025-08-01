# Current Monitor Tutorial - Forward Education
```package
fwd-smart-solar=github:Forward-Education/pxt-smart-solar#v1.0.3
```

## Sun-Tracking Solar Panel - Use Tutorial @showdialog
Today, you are going to code a monitor that measures the current (the flow of electricity) generated by your solar panel. You’ll then convert this measurement into a visual display on your micro:bit, showing you how much electricity is flowing in real-time!

<img src="https://raw.githubusercontent.com/Forward-Education/pxt-solar/main/curriculum/projects/current-monitor/render.png" alt="Current monitor solar panel render" style="display: block; width: 100%; margin:auto;">

## Step 1 @showdialog
IMPORTANT! Make sure your Breakout Board is turned on and your micro:bit is plugged into your computer.

<img src="https://raw.githubusercontent.com/Forward-Education/pxt-solar/main/curriculum/general-assets/pluganim.webp" alt="Plug micro:bit into USB port on computer" style="display: block; width: 40%; margin:auto;">

## Step 2 @showdialog
Click the three dots beside the ``|Download|`` button, then click on _Connect Device_.
Next, follow the steps to pair your micro:bit.

<img src="https://raw.githubusercontent.com/Forward-Education/pxt-solar/main/curriculum/general-assets/pairmicrobitGIF.webp"  alt="Pairing gif" style="display: block; width: 60%; margin:auto;">

## Step 3
We want our micro:bit to constantly check the current. We'll use a **loop** for this. 

Drag an ``||Loops:every 500 ms||`` loop from the ``||Loops:Loops||`` drawer into the coding workspace.

~hint Tell me more!
- A loop is a sequence of instructions that is continually repeated until a certain condition is met. Think of it like a set of instructions you tell your micro:bit to do over and over again.
hint~

```blocks
loops.everyInterval(500, function () {
	
})
```

## Step 4
Next, we'll need to use a **conditional statement** to check the current value and display a specific pattern.

From the ``||Logic:Logic||`` drawer, drag an ``||Logic:if then else||`` block into the workspace. 

~hint Tell me more!
- A conditional statement (often called an "if-then-else" statement) is a fundamental concept in programming that allows your code to _make decisions_. It's like telling your micro:bit: "IF this condition is true, THEN do this."
- We use conditional statements to make decisions in real-life, too! For example, if it is raining, then I bring my umbrella! 
hint~

```blocks
loops.everyInterval(500, function () {
    // @highlight
    if (true) {
    	
    } else {
    	
    }
})

```

## Step 5
Our first condition will be for a **non-existent or _very_ low current**. We want the code to say:

**IF** the current is low (under 0.1 mA), **THEN** show an 'X' on the micro:bit's display. How might we do this? 

## Step 6
Drag a ``||fwdSensors:current is over 0 mA ||`` block into the first part of the conditional statement (also known as the "hypothesis"). Change **over** to **under** in the dropdown. Then, change **0** to **0.1 mA**.

```blocks
loops.everyInterval(500, function () {
    // @highlight
    if (fwdSensors.current1.isPastThreshold(0.1, fwdEnums.OverUnder.Under)) {
        
    } else {
    
    }
})
```

## Step 7
Drag a ``||Basic:show icon||`` block into the conclusion of the conditional statement, so that it reads:

**THEN** show an 'X' on the micro:bit's display.

```blocks
loops.everyInterval(500, function () {
    if (fwdSensors.current1.isPastThreshold(0.1, fwdEnums.OverUnder.Under)) {
        // @highlight
        basic.showIcon(IconNames.No)
    } else {
        
    }
})
```

## Step 8
Click the '+' icon on the bottom of the conditional to create 1 new ``||logic:else if||`` statement.

```blocks
loops.everyInterval(500, function () {
    // @highlight
    if (fwdSensors.current1.isPastThreshold(0.1, fwdEnums.OverUnder.Under)) {
        basic.showIcon(IconNames.No)
    } else if (false) {
    	    	
    } else {
    	
    }
})
```

## Step 9
Now we need to create a display when the solar panel is generating a _medium strength current._ 

Right click on the first hypothesis and select 'Duplicate'. Drag this new hypothesis into the second conditional statement. Change 0.1 mA to 40 mA.

```blocks
loops.everyInterval(500, function () {
    // @highlight
    if (fwdSensors.current1.isPastThreshold(0.1, fwdEnums.OverUnder.Under)) {
        basic.showIcon(IconNames.No)
    } else if (fwdSensors.current1.isPastThreshold(40, fwdEnums.OverUnder.Under)) {
        
    } else {
       
    }
})
```

## Step 10
Drag a ``||Basic:show LEDs||`` block into the conclusion of the second conditional statement. Make nine LEDs light up on the micro:bit's display. This will indicate a medium strength current.   

~hint Tell me more!
- Remember, the LEDs are a visual representation of the strength of the current.
- Check out the lightbulb hint to see how we've solved this, but feel free to get creative with your displays!
hint~

```blocks
loops.everyInterval(500, function () {
    if (fwdSensors.current1.isPastThreshold(0.1, fwdEnums.OverUnder.Under)) {
        basic.showIcon(IconNames.No)
    } else if (fwdSensors.current1.isPastThreshold(40, fwdEnums.OverUnder.Under)) {
        // @highlight
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . # # # .
            # # # # #
            `)
    } else {
        
    }
})
```

## Step 14
Drag a ``||basic:show LEDs||`` block into the final ``||logic:else||`` condition. Make twenty-three LEDs light up on the micro:bit's display in this case. This will represent a "high" current scenario.

```blocks
loops.everyInterval(500, function () {
    if (fwdSensors.current1.isPastThreshold(0.1, fwdEnums.OverUnder.Under)) {
        basic.showIcon(IconNames.No)
    } else if (fwdSensors.current1.isPastThreshold(40, fwdEnums.OverUnder.Under)) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . # # # .
            # # # # #
            `)
    } else {
        // @highlight
        basic.showLeds(`
            . # # # .
            # # # # #
            # # # # #
            # # # # #
            # # # # #
            `)
    }
})

```

## Download
Click the ``|Download|`` button to download the code to your solar panel project and test it out!

## Reflection
Before we wrap up:
- List 2 new things you learned today.
- What is one thing you want to learn more about?

## Finished
Click the ``|Done|`` button to finish this tutorial.