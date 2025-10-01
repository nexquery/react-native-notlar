## ⚠️ ÖNEMLİ
Gerekli paketlerde icon paketini kurunca burdaki işlemlere gerek kalmıyor.  
[Icon Paket Listesi](https://oblador.github.io/react-native-vector-icons/)
```tsx
import { FontAwesome6 } from "@react-native-vector-icons/fontawesome6";
<FontAwesome6 name="rocket" size={20} color="green" iconStyle="solid" />
```


## Gerekli Paketleri Kurun
```
npm install react-native-vector-icons
npm install --save-dev @types/react-native-vector-icons
```

## Proje İçine Gerekli Dosyayı Oluşturun
```
react-native.config.js
```

## Dosyayı Açın Ve Şunları Ekleyin
```
module.exports =
{
  assets: [
      './node_modules/react-native-vector-icons/Fonts'
  ],
};
```

## Komutu Çalıştırın
```
npx react-native-asset
```

## Kullanım
```tsx
import Icon from "react-native-vector-icons/MaterialCommunityIcons";

<Icon name="wifi-off" size={45} style={styles.icon_wifi} />
```

## Gerekli Fontların Kullanılabileceği Liste
[react-native-vector-icons](https://github.com/oblador/react-native-vector-icons?tab=readme-ov-file#actively-maintained)  

### Actively maintained

- [`AntDesign`](https://ant.design/components/icon) from Ant Group (v4.4.2 with _449_ icons)
- [`Feather`](http://feathericons.com) created by Cole Bemis & Contributors (v4.29.2 featuring _287_ icons)
- [`FontAwesome 6`](https://fontawesome.com/search) designed by Fonticons, Inc. (v6.7.2 featuring _2060_ free and _52663_ pro icons)
- [`Foundation`](http://zurb.com/playground/foundation-icon-fonts-3) by ZURB, Inc. (v3.0 with _283_ icons)
- [`Ionicons`](https://ionic.io/ionicons) crafted by Ionic (v8.0.9 containing _1357_ icons)
- [`MaterialDesignIcons`](https://pictogrammers.com/library/mdi/) from MaterialDesignIcons.com (v7.4.47 including _7448_ icons)
- [`Octicons`](https://primer.style/foundations/icons) designed by GitHub, Inc. (v19.15.2 with _333_ icons)
- [`Lucide`](https://lucide.dev/) designed by Lucide, (v0.473.0 with _1548_ icons)

### No longer maintained upstream

- [`Entypo`](http://entypo.com) by Daniel Bruce (v1.0.1 with _411_ icons)
- [`EvilIcons`](http://evil-icons.io) designed by Alexander Madyankin & Roman Shamin (v1.10.1 with _70_ icons)
- [`FontAwesome`](https://fontawesome.com/v4/icons) by Fonticons, Inc. (v4.7.0 containing _785_ icons)
- [`FontAwesome 5`](https://fontawesome.com/v5/search) from Fonticons, Inc. (v5.15.4 offering _1611_ free and _7869_ pro icons)
- [`Fontisto`](https://github.com/kenangundogan/fontisto) created by Kenan Gündoğan (v3.0.4 featuring _617_ icons)
- [`MaterialIcons`](https://fonts.google.com/icons?icon.set=Material+Icons) by Google, Inc. (v4.0.0 featuring _2234_ icons)
- [`SimpleLineIcons`](https://simplelineicons.github.io/) crafted by Sabbir & Contributors (v2.5.5 with _189_ icons)
- [`Zocial`](https://smcllns.github.io/css-social-buttons) by Sam Collins (v1.1.1 with _100_ icons)
