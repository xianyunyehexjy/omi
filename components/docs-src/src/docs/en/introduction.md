## What's Omiu ?

Omiu is a cross framework UI component library developed based on [OMI](https://github.com/tencent/omi), which outputs custom elements of standard web components. Any component can be used in any framework or frameless environment such as react, Vue, preact, OMI or native JS at the same time, which is very convenient. Overall, omiu has these characteristics:

* Cross frameworks 
* High quality UI interaction details
* Integrated all the MUI Icon
* Mobile terminal and PC share one set of components
* Theme switching support at runtime (color, font, and fillets)
* Components directly decoupled, independently polished, independently released, independently quoted
* Extended HTML capabilities. You can pass false to an element through the string `'0'` or the string `'false'`

## Usage

### Install by script

```html
<script src="https://unpkg.com/omi"></script>
<script src="https://unpkg.com/@omiu/button"></script>

<o-button>I am button</o-button>
```

### Install by npm

``` bash
npm install @omiu/button
```

Import to use it:

```js
import '@omiu/button'
```

Then use it in any framework, such as Omi, react, Vue or angular:

``` html
<o-button>I am button</o-button>
```

You can also use native JS:

```js
var button = document.createElement('o-button')
button.innerHTML = 'I am omiu button'
document.body.append(button)
button.addEventListener('click', function () {
  console.log('Clicked!')
})

//or
//document.body.innerHTML = '<o-button>I am omiu button</o-button>'
```

## Change Theme

```js
const setTheme = Omiu.setTheme

setTheme('primary', '#07c160')
setTheme('danger', '#f5222d')
setTheme('surface', '#ffffff')
setTheme('on-primary', '#ffffff')
setTheme('on-danger', '#ffffff')
setTheme('on-surface', '#000000')
setTheme('background', '#ffffff')
setTheme('small-radius', '4px')
setTheme('medium-radius', '4px')
setTheme('large-radius', '0px')
setTheme('font-family', '-apple-system-font,"Helvetica Neue",sans-serif')
```

or

```js
Omiu.setThemePrimary('green')
Omiu.setThemeError('red')
```



## HTML Extension 

When the default value is true and you need to pass false to the element, it used to be a historical problem. OMI has solved this problem perfectly. You can set it through the string `'0'` or the string `'false'`.

```js
define('my-element', class extends WeElement {
  static defaultProps = {
    show: true
  }

 static propTypes = {
    show: Boolean
  }

  render(props) {
    ...
    ...
  }
})
```

Use:

```html
<my-element show="false"></my-element>
```

or

```html
<my-element show="0"></my-element>
```

## Using omiu in react

```jsx
/** @jsx nativeEvents */
import nativeEvents from 'jsx-native-events'
import { useState } from 'react'
import '@omiu/icon-button'

export default function SomeComponent(props) {
    const [result, setSwitch] = useState(false)

    return (
      <div>
        <p>The switch is {result ? 'on' : 'off'}</p>
        <o-icon-button color="red" icons="['favorite', 'favorite_border']" onEventChange={e => setSwitch(e.detail.isOn)}>
        </o-icon-button>
      </div>
    )
}
```

Many thanks to calebdwilliams's [jsx-native-events](https://github.com/calebdwilliams/jsx-native-events#readme)。

## Using omiu in Vue

```html
<script>
import '@omiu/icon-button'

export default {
  name: 'HelloWorld',
  data: function() {
    return {
      result: false
    }
  },
  methods: {
    myEvent: function(evt) {
      this.result = evt.detail.isOn
    }
  }
}
</script>

<template>
  <div class="component">
    <p>The switch is {{result? 'on' : 'off'}}</p>
    <o-icon-button color="red" icons="['favorite', 'favorite_border']" @change="myEvent"></o-icon-button>
  </div>
</template>
```


## Contribution

Build:

```bash
npm run build
```

Build Demo:

```bash
npm start 
```

Public to npm:

```bash
npm publish --access public
```

## Related links

* [material icon search](https://material-ui.com/zh/components/material-icons/) 

Converting upper case to middle dash is the corresponding omiu component. Such as `@material-ui/icons/AccessAlarm`, the omiu element is:

```js
import '@omiu/icon/access-alarm'
```

Using in html:

```html
<o-icon-access-alarm></o-icon-access-alarm>
```

So Easy!
