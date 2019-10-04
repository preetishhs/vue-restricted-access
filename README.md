# vue-restricted-access

This package is useful when you need to block certain elements/components on the page from the user to access it.
This package is fully customizable, you can change the background color, blur, opacity, status message etc by passing apropriate values to the `config` object. The package also allows the users to implement their own custom status box.

[Codesandbox Demo]()

### Example usecases: 
1. lock components and force user to login/signup to vue
2. Users with insufficient permissions

### How to install

```
npm install --save vue-restricted-access
```

### How to use

##### Import 

```js
import RestrictedAccess from 'vue-restricted-access'
```

##### Register it as a component:

```js
components: {
  RestrictedAccess
}
```

#####  Usage

Just wrap the component which you need to restrict the users from viewing and pass the `restricted` param as `true`

```html
<resrticted-access :restricted="true">
  <my-component></my-component>
</restricted-access>
```

### Config

You can also send an additional config object with any of these parameters 

```html
<restricted-access :restricted="true" :config="myConfigObj">
```

config object will take the following properties:

| Property                   | Required | Type    | Default | Description                                                                                                            |
| -------------------------- | -------- | ------- | ------- | ---------------------------------------------------------------------------------------------------------------------- |
| strict                     | false    | Boolean | false   | strict mode will fully remove the element from DOM instead of blurring it (for more sensitive contents)                |
| opacity                    | false    | Number  | 0.5     | Opacity of the overlay                                                                                                 |
| blur                       | false    | Number  | 3       | Blur radius                                                                                                            |
| showLock                   | false    | Boolean | true    | show lock icon                                                                                                         |
| statusText                 | false    | String  | ''      | Status text to display on the restricted access component                                                              |
| statusTextColor            | false    | String  | #000    | Status text color                                                                                                      |
| statusTextColor            | false    | String  | #000    | Status text color                                                                                                      |
| showStatusText             | false    | Boolean | true    | show status text                                                                                                       |
| customStatusBox            | false    | Boolean | false   | If you set custom status to `true` then you need use scoped slot with name `custom-message` to pass your own component |
| customStatusPositionCenter | false    | Boolean | true    | If this is passed true then your custom status box will be in the center                                               |

```js
//example config object
myConfigObj = {
  strict: false,
  opacity: 0.5,
  blur: 3,
  showStatusText: true,
  statusText: 'Signup to access this content',
  statusTextColor: '#000',
  showLock: true,
  customStatusBox: false,
  customStatusPositionCenter: true
}
```