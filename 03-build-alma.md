## APK İçin
Proje içindeyken konsol ekranında kullanılmalı.
```
cd android
./gradlew assembleRelease

# Build alırken hata veriyorsa bu şekilde kullanın, hatanın nerden kaynaklandığını tespit ediyor.
./gradlew assembleRelease --stacktrace
```

## Bundle İçin (Google Play veya diğer adıyla Play Store)
Proje içindeyken konsol ekranında kullanılmalı.
```
cd android
./gradlew bundleRelease
```
