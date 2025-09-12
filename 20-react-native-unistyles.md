## Kurulum
```
npm install react-native-unistyles react-native-nitro-modules react-native-edge-to-edge
```

## Ayarlar
babel.config.js
```tsx
module.exports = function (api)
{
    api.cache(true)
    return {
        presets: ['module:@react-native/babel-preset'],
        plugins: [
            'react-native-worklets/plugin',
            ['react-native-unistyles/plugin', { root: 'src' }]
        ]
    }
}
```
