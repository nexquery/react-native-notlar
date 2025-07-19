## constants.tsx
```tsx
import { NativeStackScreenProps } from "@react-navigation/native-stack";
import { BottomTabScreenProps } from "@react-navigation/bottom-tabs";

// Normal ekranlar için navigasyon ayarları
export type RootStackParamList = {
    AnaEkran: undefined;
    TabMenu: undefined;
};

// Tab ekranlar için navigasyon ayarları
export type TabParamList = {
    Profil: {
        isim: string;
    };
    Ayarlar: undefined;
};

export type StackScreenProps<RouteName extends keyof RootStackParamList> = NativeStackScreenProps<RootStackParamList, RouteName>;
export type TabScreenProps<RouteName extends keyof TabParamList> = BottomTabScreenProps<TabParamList, RouteName>;
```

## App.tsx
```tsx
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import { Button, Text, View } from 'react-native';
import { RootStackParamList, StackScreenProps, TabParamList, TabScreenProps } from './constants';
import Icon from 'react-native-vector-icons/MaterialCommunityIcons';

// Stackleri oluştur
const RootStack = createNativeStackNavigator<RootStackParamList>();
const Tab = createBottomTabNavigator<TabParamList>();

export function AnaEkran({ navigation, route }: StackScreenProps<'AnaEkran'>)
{
    return (
        <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
            <Text>Welcome Screen</Text>
            <Button title="Tab Menüye Git" onPress={() => navigation.replace('TabMenu')} />
        </View>
    )
}

function Profil({ navigation, route }: TabScreenProps<'Profil'>)
{
    return (
        <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
            <Text>Profil Adı: {route.params.isim}</Text>
        </View>
    )
}

function Ayarlar({ navigation, route }: TabScreenProps<'Ayarlar'>)
{
    return (
        <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
            <Text>Ayarlar</Text>
        </View>
    )
}

export function TabMenu({ navigation, route }: StackScreenProps<'TabMenu'>)
{
    return (
        <Tab.Navigator screenOptions={{ headerShown: false, lazy: true, animation: 'fade' }} >
            <Tab.Screen name="Profil" component={Profil} initialParams={{ isim: 'Burak' }} options={{
                tabBarLabel: 'Profil',
                tabBarIcon: ({ color, size }) => (
                    <Icon name="account" size={size} color={color} />
                )
            }} />
            <Tab.Screen name="Ayarlar" component={Ayarlar} options={{
                tabBarLabel: 'Ayarlar',
                tabBarIcon: ({ color, size }) => (
                    <Icon name="cog" size={size} color={color} />
                )
            }} />
        </Tab.Navigator>
    )
}

export default function App()
{
    return (
        <NavigationContainer>
            <RootStack.Navigator screenOptions={{ headerShown: false, animation: 'slide_from_right' }}>
                <RootStack.Screen name="AnaEkran" component={AnaEkran} />
                <RootStack.Screen name="TabMenu" component={TabMenu} />
            </RootStack.Navigator>
        </NavigationContainer>
    )
}
```

## Yeni Tab Menü
```tsx
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import { RootStackParamList, StackScreenProps, TabParamList, TabScreenProps } from './../constants';
import Icon from 'react-native-vector-icons/MaterialCommunityIcons';
import { useSafeAreaInsets } from 'react-native-safe-area-context';

// Stackleri oluştur
const RootStack = createNativeStackNavigator<RootStackParamList>();
const Tab = createBottomTabNavigator<TabParamList>();

// Normal Ekranlar
import { Karsilama_Ekrani } from './normal/karsilama_ekrani/karsilama_ekrani';

// BottomTab Ekranlar
import { AnaSayfa } from './tab/anasayfa';
import { Arama } from './tab/arama';
import { Topluluk } from './tab/topluluk';
import { Planlar } from './tab/planlar';
import { Profil } from './tab/profil';

export function Normal_Menu()
{
    return (
        <NavigationContainer>
            <RootStack.Navigator screenOptions={{ headerShown: false, animation: 'slide_from_right' }}>
                <RootStack.Screen name="Karsilama_Ekrani" component={Karsilama_Ekrani} />
                <RootStack.Screen name="TabMenu" component={TabMenu} />
            </RootStack.Navigator>
        </NavigationContainer>
    )
}

export function TabMenu({ navigation, route }: StackScreenProps<'TabMenu'>)
{
    const insets = useSafeAreaInsets();
    return (
        <Tab.Navigator screenOptions={{
                headerShown: false,
                animation: 'fade',
                tabBarShowLabel: false,
                tabBarStyle: {
                    backgroundColor: '#000000',
                    height: 50 + insets.bottom,
                },
                tabBarIconStyle: {
                    justifyContent: 'center',
                    alignItems: 'center',
                    marginTop: 5,   // ikonları aşağı indirir
                },
                tabBarItemStyle: {
                    justifyContent: 'center',
                    alignItems: 'center',
                },
            }}>
            <Tab.Screen name="AnaSayfa" component={AnaSayfa} options={{
                tabBarIcon: ({ color, size }) => (
                    <Icon name="home" size={size} color={color} />
                )
            }} />
            <Tab.Screen name="Arama" component={Arama} options={{
                tabBarIcon: ({ color, size }) => (
                    <Icon name="magnify" size={size} color={color} />
                )
            }} />
            <Tab.Screen name="Topluluk" component={Topluluk} options={{
                tabBarIcon: ({ color, size }) => (
                    <Icon name="account-group" size={size} color={color} />
                )
            }} />
            <Tab.Screen name="Planlar" component={Planlar} options={{
                tabBarIcon: ({ color, size }) => (
                    <Icon name="calendar-blank-multiple" size={size} color={color} />
                )
            }} />
            <Tab.Screen name="Profil" component={Profil} options={{
                tabBarIcon: ({ color, size }) => (
                    <Icon name="account" size={size} color={color} />
                )
            }} />
        </Tab.Navigator>
    )
}
```
