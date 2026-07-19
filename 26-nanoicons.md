## Projenin Root Klasörüne
`.nanoicons.json` dosyasını oluştur ve içine şunu ekle
```tsx
{
    "iconSets": [
        {
            "inputDir": "./src/assets/icons",
            "fontFamily": "SvgFonts",
            "outputDir": "./src/assets/nanoicons"
        }
    ]
}
```

## Svg Dosyaları
Kullanılacak svg dosyalarını `proje/src/assets/icons` içine atın daha sonra root klasöründe  
`bunx react-native-nano-icons --path .` komutunu çalıştırıp build alın

## Kullanım
```tsx
import { View, Text } from "react-native"
import { createNanoIconSet } from "react-native-nano-icons";
import glyphMap from "./assets/nanoicons/SvgFonts.glyphmap.json";

export const Icon = createNanoIconSet(glyphMap);

export default function App()
{
    return (
        <>
            <View style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
                <Text>Mocha</Text>
                <Icon name="heart" size={24} />
            </View>
        </>
    )
}
```
