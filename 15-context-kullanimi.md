## Context dosyasını oluşturun ve bunları ekleyin
```tsx
import { createContext, useContext, useState, ReactNode } from 'react';

// Props'u oluştur
interface Deneme_Props
{
    deger: number;
    setDeger: (deger: number) => void;
}

// Context'i oluştur
const Context_Deneme = createContext<Deneme_Props>(
{
    deger: 0,
    setDeger: () => { },
});

// Sağlayıcı (Provider)
export const Deneme_Provider = ({ children }: { children: ReactNode }) =>
{
    const [pDeger, setPDeger] = useState<number>(0);
    return (
        <Context_Deneme.Provider value={{ deger: pDeger, setDeger: setPDeger }}>
            {children}
        </Context_Deneme.Provider>
    )
};

// Contexi kullan
export const useDeneme = () => useContext(Context_Deneme);
```

## Provider ile kancalayın ve kullanın
```tsx
import SafeAreaViewComponent from '../components/common/SafeAreaView';
import { ScreenProps } from '../types/navigation';
import { Button, StatusBar, Text } from 'react-native';
import { useDeneme } from '../contexts/deneme';

export default function On_Yukleme({ navigation, route }: ScreenProps<'On_Yukleme'>)
{
    // contexti kullan
    const { deger, setDeger } = useDeneme();

    return (
        <Deneme_Provider>
            <SafeAreaViewComponent barStyle='light-content' useGradient={true} style={{ justifyContent: 'center', alignSelf: 'center' }}>
                <Text style={{ fontSize: 20, color: 'white' }}>{deger}</Text>

                <Button title='Artır' onPress={() => setDeger(deger + 1)} />
            </SafeAreaViewComponent>
        </Deneme_Provider>
    )
}
```
