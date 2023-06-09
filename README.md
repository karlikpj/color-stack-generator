![react](https://img.shields.io/badge/react-16.13.1-green.svg?style=flat-square)
![version](https://img.shields.io/badge/version-0.00.4-51b1c5.svg?style=flat-square)

# Color Stack Builder

<table><tr>
<td><img src='./splash.png' width=400></td>
<td><img src='./splash2.png' width=400></td>
</tr></table>

_screen shots_
[Color stack generator](http://color-stacks.surge.sh/) and tools to build, consume and work with the design tokens from the USWDS - [USWDS](https://designsystem.digital.gov/design-tokens/color/overview/)

This is a simple tool to edit and build colors stacks and export that data. You start with a base hue value, which is then spread by it's stack size and evaluates the 'grade' values.

Once a base color (or variant) is saved, you can then fine tune colors in that stack. Items that fail the gradient check - which aligns a rating to the colors based on its luminance values, will be highlighted. Those number values translate to WCAG AA/AAA contrast accessibility which is baked into the USWDS.

## Example json file for color pallete including vivid variation.

```json
{
  "global": {
    "category": "system-color-blue-cool"
  },
  "props": [
    {
      "name": "blue-cool",
      "value": [
        { "name": "5", "value": "#e7f2f5" },
        { "name": "10", "value": "#dae9ee" },
        { "name": "20", "value": "#adcfdc" },
        { "name": "30", "value": "#82b4c9" },
        { "name": "40", "value": "#6499af" },
        { "name": "50", "value": "#3a7d95" },
        { "name": "60", "value": "#2e6276" },
        { "name": "70", "value": "#224a58" },
        { "name": "80", "value": "#14333d" },
        { "name": "90", "value": "#0f191c" },
        {
          "name": "vivid",
          "value": [
            { "name": "5", "value": "#e1f3f8" },
            { "name": "10", "value": "#c3ebfa" },
            { "name": "20", "value": "#97d4ea" },
            { "name": "30", "value": "#59b9de" },
            { "name": "40", "value": "#28a0cb" },
            { "name": "50", "value": "#0d7ea2" },
            { "name": "60", "value": "#07648d" },
            { "name": "70", "value": "#074b69" },
            { "name": "80", "value": "#002d3f" },
            { "name": "90", "value": false }
          ]
        }
      ]
    }
  ],
  "options": {
    "file": "system-color"
  }
}
```

These grade values do not follow a linear scale along the luminance, rather between fixed points as listed int he table below. The colors picked by the USWDS adhear to this specification and state that the colors are not a set formal formula but manually edited to match the ratings for each grade.

| grade | minimum luminance | maximum luminance |
| ----- | :---------------: | :---------------: |
| `0`   |      `1.000`      |      `1.000`      |
| `5`   |      `0.850`      |      `0.930`      |
| `10`  |      `0.750`      |      `0.820`      |
| `20`  |      `0.500`      |      `0.650`      |
| `30`  |      `0.350`      |      `0.450`      |
| `40`  |      `0.250`      |      `0.300`      |
| `50`  |      `0.175`      |      `0.183`      |
| `60`  |      `0.100`      |      `0.125`      |
| `70`  |      `0.050`      |      `0.070`      |
| `80`  |      `0.020`      |      `0.040`      |
| `90`  |      `0.005`      |      `0.015`      |
| `100` |      `0.000`      |      `0.000`      |

#

### Note for grey_xxx color families

Not documented in their site but these grades are listed in the grey_xxx color familes. This scale has been updated with the ranges set from their palette and only applies to the grey scales.

| grade | minimum luminance | maximum luminance |
| ----- | :---------------: | :---------------: |
| `1`   |     `0.9722`      |     `0.9879`      |
| `2`   |     `0.9443`      |     `0.9722`      |
| `3`   |     `0.9204`      |     `0.9443`      |
| `4`   |     `0.8946`      |     `0.9204`      |

##

_luminance chart from uswds_

#

## How to use

Click add, edit the color by click the input/color box in the modal. Once you find a good color value (even if not all the grades work - cause they wont) - click save.

Once you have a stack on screen you can then click an individual color box to edit that one tone / grade specifically.

While you move the color selection the application will always check the luminance values

Add or Delete stacks as needed.

Stack size can only be set before you create any stacks - once there is one active or on the page / that select is disabled.

## In Development

- Consuming USWDS tokens and using a default starting point
- Contrast checker for selected colors

## To Do's:

- Import of YAML and JSON files
- Component preview

## Run the example

Requires Node v16.xx.xx or greater

```bash
$ yarn install
$ yarn start
```

open http://localhost:2020/
