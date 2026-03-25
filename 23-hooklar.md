## useCallback
Bu hook bir öğenin tekrar oluşmaması için referansını tutuyor ve render olmasını engelliyor.
Bu örnekte sayfa ilk yüklendiğinde tüm id'ler keyExtractor çağrılır.
Bundan sonraki süreçte butona bastığında sadece `console.log("Profil render oldu");` mesajı gelir.
```tsx
const data = [
    { id: 1, baslik: "Birinci" },
    { id: 2, baslik: "İkinci" },
    { id: 3, baslik: "Üçüncü" },
];

const renderItem = ({ item }: { item: typeof data[0] }) => <Text>{item.baslik}</Text>;

export function Profil({ navigation, route }: TabScreenProps<"Profil">)
{
    const [sayi, setSayi] = useState(0);

    const keyExtractor = useCallback((item: typeof data[0]) =>
    {
        console.log("keyExtractor çağrıldı:", item.id);
        return item.id.toString();
    }, []);

    // const keyExtractor = (item: typeof data[0]) =>
    // {
    //     console.log("keyExtractor çağrıldı:", item.id);
    //     return item.id.toString();
    // };

    console.log("Profil render oldu");

    return (
        <>
            <CustomSafeArea>
                <Pressable onPress={() => setSayi(sayi + 1)}>
                    <Text>Tıkla: {sayi}</Text>
                </Pressable>
                <FlashList
                    data={data}
                    renderItem={renderItem}
                    keyExtractor={keyExtractor}
                />
            </CustomSafeArea>
        </>
    );
}
```
Ama buradaki örnekte ise kullanıcı butona bassa bile keyExtractor yeniden çağrılır. Çünkü referans tutulmamış.
```tsx
const data = [
    { id: 1, baslik: "Birinci" },
    { id: 2, baslik: "İkinci" },
    { id: 3, baslik: "Üçüncü" },
];

const renderItem = ({ item }: { item: typeof data[0] }) => <Text>{item.baslik}</Text>;

export function Profil({ navigation, route }: TabScreenProps<"Profil">)
{
    const [sayi, setSayi] = useState(0);

    const keyExtractor = (item: typeof data[0]) =>
    {
        console.log("keyExtractor çağrıldı:", item.id);
        return item.id.toString();
    };

    console.log("Profil render oldu");

    return (
        <>
            <CustomSafeArea>
                <Pressable onPress={() => setSayi(sayi + 1)}>
                    <Text>Tıkla: {sayi}</Text>
                </Pressable>
                <FlashList
                    data={data}
                    renderItem={renderItem}
                    keyExtractor={keyExtractor}
                />
            </CustomSafeArea>
        </>
    );
}
```
Veya bu fonksiyonlar dış tarafada alınabilir;
```tsx
const data = [
    { id: 1, baslik: "Birinci" },
    { id: 2, baslik: "İkinci" },
    { id: 3, baslik: "Üçüncü" },
];

const renderItem = ({ item }: { item: typeof data[0] }) => <Text>{item.baslik}</Text>;

const keyExtractor = (item: typeof data[0]) =>
{
    console.log("keyExtractor çağrıldı:", item.id);
    return item.id.toString();
};

export function Profil({ navigation, route }: TabScreenProps<"Profil">)
{
    const [sayi, setSayi] = useState(0);

    console.log("Profil render oldu");

    return (
        <>
            <CustomSafeArea>
                <Pressable onPress={() => setSayi(sayi + 1)}>
                    <Text>Tıkla: {sayi}</Text>
                </Pressable>
                <FlashList
                    data={data}
                    renderItem={renderItem}
                    keyExtractor={keyExtractor}
                />
            </CustomSafeArea>
        </>
    );
}
```
