## Projeye Gerekli Dosyayı Oluşturun
```
react-native.config.js
```

## Gerekli Kodun Eklenmesi
react-native.config.js dosyasını açın ve şu kodu ekleyin.
```
module.exports = {
    assets: ['./src/assets/fonts/  -- Burası fontların bulunduğu dizin'],
};
```

## Komutu Çalıştırın
```
npx react-native-asset
```

## Kullanım
```
<Text style={{ fontFamily: 'Nunito-SemiBold', fontSize: 18 }}>
```

## Not
Sadece font adını girin, uzantılarını eklemeyin.  
  
✅ Nunito-SemiBold  
❌ Nunito-SemiBold.ttf  
