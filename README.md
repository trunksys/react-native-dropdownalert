## react-native-dropdownalert

[![Platform](https://img.shields.io/badge/platform-react--native-lightgrey.svg)](http://facebook.github.io/react-native/)
[![npm version](http://img.shields.io/npm/v/react-native-dropdownalert.svg)](https://www.npmjs.com/package/react-native-dropdownalert)
[![npm version](http://img.shields.io/npm/dm/react-native-dropdownalert.svg)](https://www.npmjs.com/package/react-native-dropdownalert)
[![Build Status](https://travis-ci.org/testshallpass/react-native-dropdownalert.svg?branch=master)](https://travis-ci.org/testshallpass/react-native-dropdownalert)
[![Join the chat at https://gitter.im/react-native-dropdownalert/Lobby](https://badges.gitter.im/react-native-dropdownalert/Lobby.svg)](https://gitter.im/react-native-dropdownalert/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.github.com/testshallpass/react-native-dropdownalert/master/LICENSE)

A simple alert to notify users about new chat messages, something went wrong or everything is ok. It can be dismissed by onPress, cancel onPress, automatically with `closeInterval` prop, pan responder up gesture or programmatically.

### Installation
```
npm i react-native-dropdownalert --save
```

### Demo
![screenshot](https://raw.github.com/testshallpass/react-native-dropdownalert/master/screenshots/demo.gif)

### Usage
```javascript

import DropdownAlert from 'react-native-dropdownalert'
// ...
render() {
  return (
    <View>
      // !!! Make sure it's the last component in your document tree.
      <DropdownAlert
        ref={(ref) => this.dropdown = ref}
        onClose={(data) => this.onClose(data)} />
    </View>
  )
}
// ...
handleRequestCallback(err, response) {
  if (err != null) {
    this.dropdown.alertWithType('error', 'Error', err)
  }
}
// ...
onClose(data) {
  // data = {type, title, message, action}
  // action means how the alert was dismissed. returns: automatic, programmatic, tap, pan or cancel
}
// ...
```

### Predefined Types

| info | warn | error | success |
| :---: | :---: | :---: | :---: |
|![screenshot](https://raw.github.com/testshallpass/react-native-dropdownalert/master/screenshots/info.png) |![screenshot](https://raw.github.com/testshallpass/react-native-dropdownalert/master/screenshots/warning.png) |![screenshot](https://raw.github.com/testshallpass/react-native-dropdownalert/master/screenshots/error.png)|![screenshot](https://raw.github.com/testshallpass/react-native-dropdownalert/master/screenshots/success.png)

### Props
| Name | Type | Description | Default |
| ---- | :---: | --- | --- |
| ```closeInterval``` | Number  | dismiss alert at a certain time in milliseconds | 4000
| ```imageSrc``` | String or Number  | local or network source | null
| ```startDelta``` | Number  | where the container starts (changes based on container height onLayout) | -100
| ```endDelta``` | Number  | where the container ends | 0
| ```onClose``` | Function  | Invoked when alert is closed Returns: ```data = {type, title, message, action}```  | null
| ```cancelBtnImageSrc``` | String or Number | local or network source | ```require('./assets/cancel.png')``` |
| ```titleNumOfLines``` | Number  | number of lines | 1
| ```messageNumOfLines``` | Number  | number of lines | 3
| ```onCancel``` | Function  | Cancel button action. Returns: ```data = {type, title, message, action}``` | null
| ```showCancel``` | Bool  | whether or not to show cancel button | false
| ```tapToCloseEnabled``` | Bool  | enable/disable close with tap | true
| ```panResponderEnabled``` | Bool  | enable/disable close with pan responder | true
| ```replaceEnabled``` | Bool  | enables the alert to either state change without dismissal or go to next alert with dismissal | true
| ```translucent``` | Bool  | StatusBar prop  | false
| ```updateStatusBar``` | Bool  | whether or not to update status bar styles  | true
| ```activeStatusBarStyle``` | String  | StatusBar barStyle when alert is open | `light-content`
| ```activeStatusBarBackgroundColor``` | String | StatusBar backgroundColor when alert is open | It takes on the backgroundColor of alert if predefined else default or provided prop
| ```inactiveStatusBarStyle``` | String  | StatusBar barStyle when alert dismisses | `StatusBar._defaultProps.barStyle.value`
| ```inactiveStatusBarBackgroundColor``` | String  | StatusBar backgroundColor when alert dismisses | `StatusBar._defaultProps.backgroundColor.value`
| ```containerStyle``` | View.propTypes.style  | styles for container for custom type only | ```{ padding: 16, flexDirection: 'row' }```
| ```titleStyle``` | Text.propTypes.style  | styles for title for all types | ```{       fontSize: 16, textAlign: 'left', fontWeight: 'bold', color: 'white', backgroundColor: 'transparent' }```
| ```messageStyle``` | Text.propTypes.style  | styles for message for all types | ```{ fontSize: 14, textAlign: 'left', fontWeight: 'bold', color: 'white', backgroundColor: 'transparent' }```
| ```imageStyle``` | Image.propTypes.style  | styles for image for all types | ```{    padding: 8, width: 36, height: 36, alignSelf: 'center' }```
| ```cancelBtnImageStyle``` | Image.propTypes.style  | styles for image for all types | ```{    padding: 8, width: 36, height: 36, alignSelf: 'center' }```
| ```successColor``` | String  | Default background color of success message | #32A54A
| ```infoColor``` | String  | Default background color of info message | #2B73B6
| ```warnColor``` | String  | Default background color of warn message | #cd853f
| ```errorColor``` | String  | Default background color of error message | #cc3232
| ```elevation``` | Number  | Animated.View elevation | 1
| ```onPress``` | func  | when Alert onPress callback  | () => {}

> Inspired by: [RKDropdownAlert](https://github.com/cwRichardKim/RKDropdownAlert)
