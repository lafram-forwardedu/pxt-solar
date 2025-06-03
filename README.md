# pxt-solar

Solar Kit, by Forward Education

Find us at [forwardedu.com](https://forwardedu.com/) and [learn.forwardedu.com](https://learn.forwardedu.com/). Learn more about the Hydroponics Kit on the [product page]().

## Example Usage

Our learning systems are designed to simplify teaching coding and computer science for educators at all experience levels.
Our Solar Kit can be used on its own or joined with other kits to access our wider library of sensors, motors, lights, and buttons.
Check out our lesson catalogue for curriculum-aligned lessons, including educator notes.
A sample of coding with the Solar Kit can be seen below.

The solar panel is charging a battery and the energy meter is between it.
When the current and voltage is above an acceptable level a happy face is shown. If not a sad face is shown.
The current and voltage readings can be displayed on demand using the micro:bit buttons and screen.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(sensors.current1.current())
})
input.onButtonPressed(Button.B, function () {
    basic.showNumber(sensors.voltage1.voltage())
})
basic.forever(function () {
    if (sensors.current1.isPastThreshold(100, sensors.ThresholdDirection.Over) && sensors.voltage1.isPastThreshold(2, sensors.ThresholdDirection.Over)) {
        basic.showIcon(IconNames.Happy)
    } else {
        basic.showIcon(IconNames.Sad)
    }
})
```

## Supported Targets

-   for PXT/microbit

## License

MIT
