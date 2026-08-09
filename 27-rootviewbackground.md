### Bilgi
Gözükecek ekrana renk atanmazsa siyah veya beyaz ekran gözükür.  
Bu çözüm https://github.com/software-mansion/react-native-screens/issues/1968 bağlantısından referans alınmıştır.

### Oluştur
`android\app\src\main\res\drawable\alpha_screen.xml`
```xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:opacity="opaque">
    <item android:gravity="fill">
        <color android:color="@android:color/transparent" />
    </item>
</layer-list>
```

### Oluştur
`android\app\src\main\res\values\styles.xml`
```xml
<resources>
    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.DayNight.NoActionBar">
        <!-- Customize your theme here. -->
        <item name="android:editTextBackground">@drawable/rn_edit_text_material</item>
+       <item name="android:windowBackground">@drawable/alpha_screen</item>
    </style>
</resources>
```

### Test
```tsx
const RootStack = createNativeStackNavigator({
    screenOptions: {
        headerShown: false,
        animation: 'default',
        contentStyle: {
            // backgroundColor: 'aqua',
        }
    },
    screens: {
        AnaEkran: createNativeStackScreen({
            screen: AnaEkran,
            options: {
                contentStyle: {
                    backgroundColor: 'green',
                }
            }
        }),

        GuncellemeEkrani: createNativeStackScreen({
            screen: GuncellemeEkrani,
            options: {
                contentStyle: {
                    backgroundColor: 'aqua',
                }
            }
        }),
    },
});
```
