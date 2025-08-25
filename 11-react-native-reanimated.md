## Animasyonlu Efektler İçin
```
npm install react-native-gesture-handler react-native-worklets react-native-reanimated
```

## babel.config.js
Plugin arrayinde her zaman en sonda olmalı.
```
module.exports = {
  presets: ['module:@react-native/babel-preset'],
  plugins: ['react-native-worklets/plugin'],
  //plugins: ['react-native-reanimated/plugin'],
};
```
