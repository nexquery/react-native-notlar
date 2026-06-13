## Basit Ekran
Basit bir react navigation örneği
```tsx
import { Text, StatusBar, Pressable, Alert } from 'react-native';
import { SafeAreaView } from 'react-native-safe-area-context';
import { createStaticNavigation, StaticScreenProps, useNavigation } from '@react-navigation/native';
import { createNativeStackNavigator, createNativeStackScreen } from '@react-navigation/native-stack';
import { AppInitializer } from './components/AppInitializer';
import { useEffect } from 'react';

function AnaEkran({ route } : StaticScreenProps<{ post?: string }>) {
    const navigation = useNavigation();

    useEffect(() => {
        if (route.params?.post) {
            Alert.alert('Yeni gönderi: ' + route.params?.post);
            
            navigation.setParams({ post: undefined });
        }
    }, [route.params?.post]);

    return (
        <SafeAreaView style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
            <Text>Ana Ekran</Text>

            <Pressable onPress={() => navigation.navigate('GuncellemeEkrani', { isim: 'Burak' })}>
                <Text>Güncelleme Ekrani</Text>
            </Pressable>
        </SafeAreaView>
    );
}

type GuncellemeEkraniRoute = {
    isim: string;
};

function GuncellemeEkrani({ route }: StaticScreenProps<GuncellemeEkraniRoute>) {
    const navigation = useNavigation('GuncellemeEkrani');
    
    return (
        <SafeAreaView style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
            <Text>Güncelleme Ekranı {route.params.isim}</Text>

            <Pressable onPress={() => navigation.popTo('AnaEkran', { post: 'Yeni post' })}>
                <Text>Geri</Text>
            </Pressable>
        </SafeAreaView>
    );
}

const RootStack = createNativeStackNavigator({
    screenOptions: {
        headerShown: false,
    },
    screens: {
        AnaEkran: createNativeStackScreen({
            screen: AnaEkran,
        }),

        GuncellemeEkrani: createNativeStackScreen({
            screen: GuncellemeEkrani,
        }),
    },
});

const Navigation = createStaticNavigation(RootStack);

export default function App() {
    return (
        <>
            <StatusBar barStyle="dark-content" />
            <AppInitializer>
                <Navigation />
            </AppInitializer>
        </>
    );
}

type RootStackType = typeof RootStack;

declare module '@react-navigation/core' {
  interface RootNavigator extends RootStackType {}
}
```
