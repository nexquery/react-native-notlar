## Bu context ekranın yönünü otomatik algılar
```<EkranYonuProvider>``` ile App kısmında sarmalanmalıdır.
```tsx
import { createContext, useContext, useState, ReactNode, useEffect } from 'react';
import { Dimensions } from 'react-native';

interface EkranYonuProps
{
    dikey: boolean;
    yatay: boolean;
}

const EkranYonuContext = createContext<EkranYonuProps>(
{
    dikey: false,
    yatay: false
});

// Dikey mi kontrol eder
function isPortrait() {
    const boyut = Dimensions.get('screen');
    return boyut.height >= boyut.width;
}

// Yatay mı kontrol eder
function isLandscape() {
    const boyut = Dimensions.get('screen');
    return boyut.width >= boyut.height;
}

function updateEkran(setDikey: (value: boolean) => void, setYatay: (value: boolean) => void)
{
    if(isPortrait())
    {
        setDikey(true);
        setYatay(false);
    }
    else if(isLandscape())
    {
        setYatay(true);
        setDikey(false);
    }
}

export const EkranYonuProvider = ({ children }: { children: ReactNode }) =>
{
    const [dikey, setDikey] = useState<boolean>(false);
    const [yatay, setYatay] = useState<boolean>(false);

    useEffect(() =>
    {
        updateEkran(setDikey, setYatay);

        const dinleyici = Dimensions.addEventListener('change', () =>
        {
            updateEkran(setDikey, setYatay);
        })

        return () =>
        {
            dinleyici.remove();
        }

    }, [])

    return (
        <EkranYonuContext.Provider value={{ dikey: dikey, yatay: yatay }}>
            {children}
        </EkranYonuContext.Provider>
    )
};

export const useEkran = () => useContext(EkranYonuContext);
```
