# vue-restricted-access

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

```js
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