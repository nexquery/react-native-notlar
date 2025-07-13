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
