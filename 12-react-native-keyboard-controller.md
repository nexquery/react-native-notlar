## Nedir?
Bir inputa focus yapıldığında klavye üstünde düzgün gözükecek şekilde inputu kaydırır.

## Kurulum
```
npm install react-native-keyboard-controller
```

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
