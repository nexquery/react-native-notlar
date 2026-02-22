## Bazen Uygulama Hata Verirse Kullanılabilir
```
cd android
./gradlew clean
cd ..
npx react-native start --reset-cache
CTRL + C (uygulamayı kapatmak için)
npx react-native run-android
```

## Eğer Klasör Dizini Değiştirirseniz
Bağımlılıkları yeniden yüklemeniz gerekir. Bunun için **node_modules** klasörünü ve **package-lock.json** dosyasını silin.  
Son olarak **npm install** komutunu çalıştırın.

## Ninja clean sorunu çözüm
**android/app/build.gradle** en altına
```
tasks.whenTaskAdded { task ->
    if (task.name.contains('externalNativeBuildClean')) {
        task.enabled = false
    }
}
```
kodunu ekle daha sonra manuel olarak **android/app/.cxx** klasörünü sil
