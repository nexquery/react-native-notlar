## Blurlu tasarımlar yapmak için
```
npm install @react-native-community/blur
```

## Örnek
```tsx
import { ImageBackground, StyleSheet, Text, View } from "react-native";
import { BlurView } from '@react-native-community/blur';

export default function App() {
  return (
        <View style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
            <ImageBackground source={{ uri: 'https://avatars.githubusercontent.com/u/39802870?v=4' }} style={{ width: '100%', height: 300, justifyContent: 'center', alignItems: 'center' }} >
                
                {/* Bu kısım ve üstü blurlu */}
                <BlurView enabled={true} style={{ position: 'absolute', top: 0, left: 0, bottom: 0, right: 0 }} blurType="light" blurAmount={20} reducedTransparencyFallbackColor="white"/>
                
                {/* Bu kısım ve altı blursuz */}
                <View style={{ justifyContent: "center", alignItems: "center", alignContent: "center", alignSelf: "center" }}>
                    <Text style={{ color: 'white', fontSize: 20 }}>Blurlu Görsel Üzerindeki Yazı</Text>
                </View>
            </ImageBackground>
        </View>
    );
}
```
