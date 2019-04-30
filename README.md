# s-alert or SimpleAlert
s-alert or SimpleAlert is a web component for displaying alert messages to the users, it is light-weight and simple to use.


## Dependency

This web component uses [domExtend](https://github.com/KirkGarcia182/domExtend)


## Usage



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
