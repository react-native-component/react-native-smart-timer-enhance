# react-native-smart-timer-enhance
A TimerEnhance for React Native app (es6) which replaced TimerMixin (es5) provides timer functions for executing code in the future that are safely cleaned up when the component unmounts

Inspired by [react-timer-mixin][0]

## Installation

```
npm install react-native-smart-timer-enhance --save
```

## Usage

Install the TimerEnhance from npm with `npm install react-native-smart-timer-enhance --save`.
Then, require it from your app's JavaScript files with `import TimerEnhance from 'react-native-smart-timer-enhance'`.

```js
import React, {
    Component,
} from 'react'

import TimerEnhance from 'react-native-smart-timer-enhance'

class TimerEnhanceDemo extends Component {

    componentDidMount() {
        this.setTimeout(() => {
            console.log('setTimeout do not leak!');
        }, 3000);
        this.setInterval( () => {
            console.log('setInterval do not leak!');
        }, 1000)
        this.requestAnimationFrame(this._raf)
    }

    render() {
        return null
    }

    _raf = (...p) => {
        console.log('requestAnimationFrame do not leak!');
        this.requestAnimationFrame(this._raf)
    }
}

export default TimerEnhance(TimerEnhanceDemo)
```

[0]: https://github.com/reactjs/react-timer-mixin
