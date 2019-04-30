# s-alert or SimpleAlert

s-alert or SimpleAlert is a web component for displaying alert messages to the users, it is light-weight and simple to use. Just create the 's-alert' element, add the props and append it to your very own alertHolder. The alert shown is timed and will fade away after the given time. The user can hover on the alert to pause the timer to let them read the message clearly.

##
## Dependency

This web component uses [domExtend](https://github.com/KirkGarcia182/domExtend). A light-weight javascript library for helping web components easier and faster.

##
## Usage

```javascript
// create the s-alert element, add the properties using props method and append it to an alert holder of your design
$.ce('s-alert')
.props(propsObject)
.appendTo(alertHolderElement);
```

##
## Props Parameters

propsObject - is an object that should contain the following
* type - A `String` that contains the type of the alert being shown. There are only 4 possible values `success`, `warning`, `danger` and `info`.
* message - A `String` that will be shown in the alert.
* time - An `Integer` that represents the time (in milliseconds) the alert will be shown, the alert will fade away after the time set.

##
## Example

index.html
```html
<!DOCTYPE html>
<html lang='en'>
<head>
    <meta charset='UTF-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1.0'>
    <meta http-equiv='X-UA-Compatible' content='ie=edge'>
    <title>Simple Alert Example</title>
    <style>
        html, body{
		    width: 100%;
		    height: 100%;
		    margin: 0;
		    font-family: var(--font-family);
		    font-size: var(--font-size);
		    background-color: var(--primary-bg-color);
		    color: var(--primary-color);
		}

		#app{
		    width: 100%;
		    height: 100%;
		}

		.alertHolder{
		    display: flex;
		    flex-direction: column;
		    position: fixed;
		    bottom: 5px;
		    right: 5px;
		    max-width: 300px;
		    z-index: 200;
		}
    </style>
</head>
<body>
    <div id='app'>
        <button id='alertMe'>Click Me To Display an Alert</button>
        <div class='alertHolder'></div>
    </div>
    <script type='module' src='./js/index.js'></script>
</body>
</html>
```

index.js
```javascript
import './js/domExtend.min.js';
import './js/s-alert.min.js';

let button = $.byId('alertMe'),
alertHolder = $.byClass('alertHolder')[0];

button.on('click', e => {
    // create a s-alert element
    $.ce('s-alert')
    
    /*
        set s-alert props by calling the props function
        only 3 props are needed
        * type - values should be either 'success', 'info', 'warning' and 'danger'
        * message - the message shown upon alert pop-up
        * time - the time (in milliseconds) before the alert fades away
    */
    .props({
        type: 'success',
        message: 'You have successfully updated your profile!',
        time: 5000
    })
    
    // append it to your alert holder
    .appendTo(alertHolder);
}
```
