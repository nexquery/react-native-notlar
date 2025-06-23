## Nedir ?
Status Bar kısmının boyutu kadar boşluk vermesini sağlar ama **Safe-Area** kullanmak daha güvenli ve mantıklıdır.

## Kullanım
```tsx
import { StyleSheet, StatusBar } from 'react-native';

const styles = StyleSheet.create(
{
  container: {
    flex: 1,
    paddingTop: StatusBar.currentHeight, // StatusBar yüksekliği kadar boşluk ekler
  },
});
```
