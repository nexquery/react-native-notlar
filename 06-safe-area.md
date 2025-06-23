## Nedir Bu?
Telefonun güvenli alanlarını alır. Yani çentik üstünde değilde çentiğin biraz altına dinamik olarak yerleştirme yapılabilir. Aynı şekil fiziksel tuşların en alt kısmı içinde geçerlidir.

## Kullanım
```tsx
import { useSafeAreaInsets } from 'react-native-safe-area-context';

const insets = useSafeAreaInsets();

bottom: insets.bottom; // Fiziksel tuşlarda boşluk bırakmaz
```
