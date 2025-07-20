## Blurlu tasarımlar yapmak için
```
npm install @react-native-community/blur
```

## Örnek
```tsx
import { Text, View, StyleSheet, StatusBar, ImageBackground } from "react-native";
import LinearGradient from "react-native-linear-gradient";
import { BlurView } from "@react-native-community/blur";

export default function App()
{
    return (
        <>
            <StatusBar animated={true} translucent={true} backgroundColor={"transparent"} barStyle={"light-content"} />
            <ImageBackground style={styles.container} source={{ uri: "https://images.pexels.com/photos/3214944/pexels-photo-3214944.jpeg?_gl=1*14i86kh*_ga*NjMxNDI4MjY2LjE3NDg1MDUyNzA.*_ga_8JE65Q40S6*czE3NTI5MzgzMjgkbzIkZzEkdDE3NTI5MzgzMzckajUxJGwwJGgw" }}>
            <View style={styles.blurWrapper}>
                <BlurView style={StyleSheet.absoluteFill} blurType="light" blurAmount={20} reducedTransparencyFallbackColor="white" />
                <Text style={styles.text}>DIYET ZAMANI</Text>
            </View>

            <View style={styles.blurWrapper}>
                <BlurView style={StyleSheet.absoluteFill} blurType="dark" blurAmount={10} reducedTransparencyFallbackColor="white" />
                <Text style={styles.text}>DIYET ZAMANI</Text>
            </View>
            </ImageBackground>
        </>
    )
}

const styles = StyleSheet.create(
{
    container: {
        flex: 1,
        justifyContent: "center",
        alignItems: "center",
    },

    blurWrapper: {
        width: 300,
        height: 200,
        justifyContent: "center",
        alignItems: "center",
        borderRadius: 20,
        overflow: 'hidden',
        backgroundColor: 'rgba(255,255,255,0.01)',
        marginBottom: 20,
    },

    text: {
        fontSize: 20,
        fontWeight: 'bold',
        color: 'yellow',
        textAlign: 'center',
    }
});
```

## Tüm Ekranı Kaplayan Blur
```tsx
export default function App()
{
    return (
        <>
            <StatusBar animated={true} translucent={true} backgroundColor={"transparent"} barStyle={"light-content"} />
            <ImageBackground style={styles.container} source={{ uri: "https://images.pexels.com/photos/3214944/pexels-photo-3214944.jpeg?_gl=1*14i86kh*_ga*NjMxNDI4MjY2LjE3NDg1MDUyNzA.*_ga_8JE65Q40S6*czE3NTI5MzgzMjgkbzIkZzEkdDE3NTI5MzgzMzckajUxJGwwJGgw" }}>

            // blur: {
            //     position: "absolute",
            //     top: 0,
            //     left: 0,
            //     right: 0,
            //     bottom: 0,
            // }
            <BlurView style={StyleSheet.absoluteFill} blurType="dark" blurAmount={10} reducedTransparencyFallbackColor="dark" />
            </ImageBackground>
        </>
    )
}
```
