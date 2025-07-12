## Nedir?
Bir inputa focus yapıldığında klavye üstünde düzgün gözükecek şekilde inputu kaydırır.

## Kurulum
```
npm install react-native-keyboard-controller
```

## build.gradle Ayarı
Derlerken hata oluşmaması için bu ayarın yapılması gereklidir
```gradle
android/app/build.gradle:
{
    // apply plugin: "com.android.application"
    // apply plugin: "org.jetbrains.kotlin.android"
    // apply plugin: "com.facebook.react"
    // import org.apache.tools.ant.taskdefs.condition.Os

    // En başa import et
    import org.apache.tools.ant.taskdefs.condition.Os

    // Bu bloğun içine 
    android
    {
        defaultConfig {
            // Ekle
            externalNativeBuild {
                cmake {
                    def cmakeDir = "${android.sdkDirectory}/cmake/3.22.1/bin" // 3.22.1 sürüm numarasını değiştirmeyi unutma
                    def ninjaExecutable = Os.isFamily(Os.FAMILY_WINDOWS) ? "ninja.exe" : "ninja"
                    def ninjaPath = "${cmakeDir}/${ninjaExecutable}".replace("\\", "/")
                    arguments "-DCMAKE_MAKE_PROGRAM=${ninjaPath}",
                            "-DCMAKE_OBJECT_PATH_MAX=1024"
                }
            }
        }
    }
}
```

## Uzun Yol Özelliğin Aktifleştir
PowerShell'i yönetici çalıştırarak bu komutu girin.
```
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
```


## Ek Paketler
[Reanimated](11-react-native-reanimated.md) kütüphanesi gereklidir.

## Kullanım
```tsx
import { SafeAreaView, StatusBar, TextInput } from 'react-native';
import { KeyboardAwareScrollView, KeyboardProvider } from 'react-native-keyboard-controller';

export default function App() {
    return (
        <KeyboardProvider>
            <StatusBar barStyle={"dark-content"} translucent={true} backgroundColor="transparent" animated={true} />
            <SafeAreaView style={{ flex: 1, backgroundColor: '#ffffff', padding: '5%' }}>
                <KeyboardAwareScrollView
                    bottomOffset={40} // Input klavyeden neden yüksekte olsun ?
                    enabled={true}
                    keyboardDismissMode="interactive"
                    keyboardShouldPersistTaps="handled"
                >
                    {Array.from({ length: 100 }, (_, index) => (
                        <TextInput key={index} placeholder={`Array ${index + 1}`} style={{
                            width: '95%',
                            marginTop: 20,
                            marginHorizontal: '2.5%',
                            borderColor: 'gray',
                            borderRadius: 5,
                            borderWidth: 0.5,
                            padding: 10
                        }}/>
                    ))}
                </KeyboardAwareScrollView>
            </SafeAreaView>
        </KeyboardProvider>
    )
}
```
