# InputNumber

### Intro

Control the number increase or decrease by clicking the button.

### Install

``` ts
// react
import { InputNumber } from '@nutui/nutui-react';
```

### Basic Usage

Initialize a default value

:::demo
```tsx
import React, { useState } from "react";
import { InputNumber } from '@nutui/nutui-react';

const App = () => {
  const [inputState, setInputState] = useState({
    val: 1,
  })
  return (
    <>
      <InputNumber modelValue={inputState.val} />
    </>
  )
}
export default App;
```
:::

### Step size setting

Set step  `step` 5 

:::demo
```tsx
import React, { useState } from "react";
import { InputNumber } from '@nutui/nutui-react';

const App = () => {
  const [inputState, setInputState] = useState({
    val: 0,
  })
  return (
    <>
      <InputNumber modelValue={inputState.val} step="5" />
    </>
  )
}
export default App;
```
:::

### Limit input range

`min` and `max` attributes represent the minimum and maximum values respectively

:::demo
```tsx
import React, { useState } from "react";
import { InputNumber, Toast } from '@nutui/nutui-react';

const App = () => {
  const [inputState, setInputState] = useState({
    val: 10,
  })
  const overlimit = (e: MouseEvent) => {
    console.log(e)
    Toast.warn('Exceeded limit event triggered')
  }
  return (
    <>
      <InputNumber modelValue={inputState.val} min="10" max="20" onOverlimit={overlimit} />
    </>
  )
}
export default App;
```
:::

### Disabled state

`disabled` When disabled, you cannot click the button or modify the input box.

:::demo
```tsx
import React, { useState } from "react";
import { InputNumber } from '@nutui/nutui-react';

const App = () => {
  const [inputState, setInputState] = useState({
    val: 0,
  })
  return (
    <>
      <InputNumber modelValue={inputState.val} disabled />
    </>
  )
}
export default App;
```
:::

### Read only disable input box

`readonly` Set read-only disable input box input behavior

:::demo
```tsx
import React, { useState } from "react";
import { InputNumber } from '@nutui/nutui-react';

const App = () => {
  const [inputState, setInputState] = useState({
    val: 1,
  })
  return (
    <>
      <InputNumber modelValue={inputState.val} readonly />
    </>
  )
}
export default App;
```
:::

### Support decimal point

Set step size `step` 0.1  `decimal-places` keep 1 decimal place

:::demo
```tsx
import React, { useState } from "react";
import { InputNumber } from '@nutui/nutui-react';

const App = () => {
  const [inputState, setInputState] = useState({
    val: 5.5,
  })
  return (
    <>
      <InputNumber modelValue={inputState.val} step="0.1" decimalPlaces="1" readonly />
    </>
  )
}
export default App;
```
:::
### Support asynchronous modification

Asynchronous modification through `change` event and `model-value`

:::demo
```tsx
import React, { useState } from "react";
import { InputNumber, Toast } from '@nutui/nutui-react';

const App = () => {
  const [inputState, setInputState] = useState({
    val: 1,
  })
  const onChange = (value: string | number) => {
    Toast.loading('Asynchronous demo changes after 2 seconds')
    setTimeout(() => {
      inputState.val7 = Number(value)
      setInputState({ ...inputState })
      Toast.hide()
    }, 2000)
  }
  return (
    <>
      <InputNumber modelValue={inputState.val} onChangeFuc={onChange} isAsync />
    </>
  )
}
export default App;
```
:::

### Custom button size

:::demo
```tsx
import React, { useState } from "react";
import { InputNumber } from '@nutui/nutui-react';

const App = () => {
  const [inputState, setInputState] = useState({
    val: 1,
  })
  return (
    <>
      <InputNumber modelValue={inputState.val} buttonSize="30" inputWidth="50" />
    </>
  )
}
export default App;
```
:::

### support formatter

:::demo
```tsx
import React from "react";
import { InputNumber } from '@nutui/nutui-react';

const App = () => {
  return (
    <>
      <InputNumber
        style={{"--nutui-inputnumber-input-width": "60px"}}
        modelValue="1000"
        min={10}
        max={15020}
        formatter={(value) =>
          `$ ${value}`.replace(/\B(?=(\d{3})+(?!\d))/g, ',')
        }
      />
      <InputNumber
        style={{"--nutui-inputnumber-input-width": "60px"}}
        modelValue="100"
        min={0}
        max={100}
        formatter={(value) => `${value}%`}
      />
    </>
  )
}
export default App;
```
:::

## API

### Props

| Attribute           | Description                       | Type           | Default     |
|----------------|----------------------------|----------------|------------|
| modelValue        | Initial value                     | string \| number | -          |
| inputWidth    | Input box width                 | string         | `40px`     |
| buttonSize    | Operators +, - Dimensions             | string         | `20px`     |
| min            | Minimum limit                 | string \| number | `1`        |
| max            | Maximum limit                 | string \| number | `9999` |
| step           | step                       | string \| number | `1`        |
| decimalPlaces | Set reserved decimal places           | string \| number | `0`        |
| disabled       | Disable all features               | boolean        | `false`      |
| readonly       | Read only status disables input box operation behavior | boolean        | `false`      |
| isAsync       | Support for asynchronous modification | boolean        | `false`      |
| formatter`v1.4.14`       | Specifies the format of the value displayed in the input box | function(value: number | string): string        | -     |

### Events

| Event    | Description                   | Arguments                       |
|-----------|------------------------|--------------------------------|
| add    `v1.3.8 Abandon`   | Triggered when the Add button is clicked     | `event: Event`                   |
| reduce   `v1.3.8 Abandon` | Triggered when the decrease button is clicked     | `event: Event`                   |
| overlimit `v1.3.8 Abandon` | Triggered when an unavailable button is clicked | `event: Event`                   |
| change `v1.3.8 Abandon`    | Triggered when the value changes           | `value: number, event: Event` |
| blur `v1.3.8 Abandon`      | Triggered when the input box blur   | `event: Event`                   |
| focus `v1.3.8 Abandon`     | Triggered when the input box focus   | `event: Event`                   |
| onAdd `v1.3.8`       | Triggered when the Add button is clicked     | `event: Event`                   |
| onReduce `v1.3.8`    | Triggered when the decrease button is clicked     | `event: Event`                   |
| onOverlimit `v1.3.8` | Triggered when an unavailable button is clicked | `event: Event`                   |
| onChangeFuc `v1.3.8`    | Triggered when the value changes           | `value: number, event: Event` |
| onBlurFuc `v1.3.8`      | Triggered when the input box blur   | `event: Event`                   |
| onFocus `v1.3.8`     | Triggered when the input box focus   | `event: Event`                   |

## Theming

### CSS Variables

The component provides the following CSS variables, which can be used to customize styles. Please refer to [ConfigProvider component](#/en-US/component/configprovider).

| Name | Default Value |
| --- | --- |
| --nutui-inputnumber-button-width`v1.4.8` | `12px` |
| --nutui-inputnumber-button-height`v1.4.8` | `12px` |
| --nutui-inputnumber-button-border-radius`v1.4.8` | `30px` |
| --nutui-inputnumber-button-background-color`v1.4.8` | `$gray6` |
| --nutui-inputnumber-icon-color | `$title-color` |
| --nutui-inputnumber-icon-void-color | `$disable-color` |
| --nutui-inputnumber-icon-disabled-color | `$gray2` |
| --nutui-inputnumber-icon-size | `20px` |
| --nutui-inputnumber-input-font-size | `12px` |
| --nutui-inputnumber-input-font-color | `$gray1` |
| --nutui-inputnumber-input-background-color | `$gray4` |
| --nutui-inputnumber-input-border-radius | `4px` |
| --nutui-inputnumber-input-width | `40px` |
| --nutui-inputnumber-input-height | `24px`|
| --nutui-inputnumber-input-margin | `0 6px` |
| --nutui-inputnumber-input-border | `0` |
| --nutui-inputnumber-border | `0` |
| --nutui-inputnumber-border-radius | `0` |
| --nutui-inputnumber-height | `auto` |
| --nutui-inputnumber-line-height | `normal` |
| --nutui-inputnumber-border-box | `content-box` |
| --nutui-inputnumber-display | `flex` |
