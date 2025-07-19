## Responsive Tasarım
Belirli bir ekran boyutunu referans alıp tüm telefonlar için pixel bazında bu referansı kullanıp tüm telefon ekranlarıyla uyumlu tasarımlar oluşturmaya yarar.

## Yeni
```tsx
import { Dimensions, PixelRatio } from 'react-native';

const DESIGN_SHORT = 375; // iPhone X gibi kısa kenar

const getShortDimension = () => {
    const { width, height } = Dimensions.get('window');
    return Math.min(width, height);
};

// Genel bütün tasarımlar için
export const sp = (size: number) => {
    const scale = getShortDimension() / DESIGN_SHORT;
    return Math.round(PixelRatio.roundToNearestPixel(size * scale));
};

// Fontlar için
export const fp = (size: number, min = 12, max = 28) =>
{
    const scale = getShortDimension() / DESIGN_SHORT;
    const scaledSize = size * scale;
    return Math.round(Math.min(Math.max(PixelRatio.roundToNearestPixel(scaledSize), min), max));
};
```

## Eski
```tsx
import { Dimensions, PixelRatio } from 'react-native';

// Ekran boyutlarını al
const { width: SCREEN_WIDTH, height: SCREEN_HEIGHT } = Dimensions.get('window');

// 2025'te en yaygın mobil ekran boyutları
// 375×812 (iPhone X ve benzeri modeller), -- En çok yaygın olan
// 414×896 (iPhone 11 gibi),
// 390×844 (iPhone 14 Pro),
// 360×640 (düşük segment Android)
// ve 412×915 (orta segment Android)

// Referans boyutlar (tasarım yaptığınız ekran boyutları)
// iPhone 12 Pro boyutlarını referans alıyoruz (390x844)
const REFERENCE_WIDTH: number = 375;
const REFERENCE_HEIGHT: number = 812;

// Cihaz tipi enum'u
export enum DeviceType {
  SMALL = 'small',
  MEDIUM = 'medium',
  LARGE = 'large',
  TABLET = 'tablet',
}

// Ekran bilgileri interface'i
export interface ScreenInfo {
  screenWidth: number;
  screenHeight: number;
  isSmallScreen: boolean;
  isMediumScreen: boolean;
  isLargeScreen: boolean;
  isTablet: boolean;
  pixelRatio: number;
  fontScale: number;
}

/**
 * Genişlik için responsive fonksiyon
 * @param size - Tasarımda kullandığınız pixel değeri
 * @returns Cihaza uygun ölçeklenmiş değer
 */
export const wp = (size: number): number => {
  const percentage: number = (size / REFERENCE_WIDTH) * 100;
  return PixelRatio.roundToNearestPixel((percentage * SCREEN_WIDTH) / 100);
};

/**
 * Yükseklik için responsive fonksiyon
 * @param size - Tasarımda kullandığınız pixel değeri
 * @returns Cihaza uygun ölçeklenmiş değer
 */
export const hp = (size: number): number => {
  const percentage: number = (size / REFERENCE_HEIGHT) * 100;
  return PixelRatio.roundToNearestPixel((percentage * SCREEN_HEIGHT) / 100);
};

/**
 * Font boyutu için responsive fonksiyon
 * @param size - Tasarımda kullandığınız font boyutu
 * @returns Cihaza uygun ölçeklenmiş font boyutu
 */
export const fp = (size: number): number => {
  const scale: number = SCREEN_WIDTH / REFERENCE_WIDTH;
  const newSize: number = size * scale;
  return Math.round(PixelRatio.roundToNearestPixel(newSize));
};

/**
 * Minimum ve maksimum değerleri olan responsive fonksiyon
 * @param size - Tasarımda kullandığınız pixel değeri
 * @param minSize - Minimum değer
 * @param maxSize - Maksimum değer
 * @returns Sınırlandırılmış responsive değer
 */
export const wpLimited = (
  size: number,
  minSize: number = 0,
  maxSize: number = Infinity
): number => {
  const responsiveSize: number = wp(size);
  return Math.max(minSize, Math.min(maxSize, responsiveSize));
};

/**
 * Yükseklik için sınırlandırılmış responsive fonksiyon
 * @param size - Tasarımda kullandığınız pixel değeri
 * @param minSize - Minimum değer
 * @param maxSize - Maksimum değer
 * @returns Sınırlandırılmış responsive değer
 */
export const hpLimited = (
  size: number,
  minSize: number = 0,
  maxSize: number = Infinity
): number => {
  const responsiveSize: number = hp(size);
  return Math.max(minSize, Math.min(maxSize, responsiveSize));
};

/**
 * Genel responsive fonksiyon (en küçük ölçek faktörünü kullanır)
 * @param size - Tasarımda kullandığınız pixel değeri
 * @returns Cihaza uygun ölçeklenmiş değer
 */
export const rp = (size: number): number => {
  const widthScale: number = SCREEN_WIDTH / REFERENCE_WIDTH;
  const heightScale: number = SCREEN_HEIGHT / REFERENCE_HEIGHT;
  const scale: number = Math.min(widthScale, heightScale);
  return PixelRatio.roundToNearestPixel(size * scale);
};

/**
 * Ekran bilgilerini döndüren yardımcı fonksiyon
 * @returns Ekran bilgileri
 */
export const getScreenInfo = (): ScreenInfo => ({
  screenWidth: SCREEN_WIDTH,
  screenHeight: SCREEN_HEIGHT,
  isSmallScreen: SCREEN_WIDTH < 350,
  isMediumScreen: SCREEN_WIDTH >= 350 && SCREEN_WIDTH < 400,
  isLargeScreen: SCREEN_WIDTH >= 400,
  isTablet: SCREEN_WIDTH > 768,
  pixelRatio: PixelRatio.get(),
  fontScale: PixelRatio.getFontScale(),
});

/**
 * Cihaz tipini döndüren fonksiyon
 * @returns Cihaz tipi
 */
export const getDeviceType = (): DeviceType => {
  if (SCREEN_WIDTH < 350) return DeviceType.SMALL;
  if (SCREEN_WIDTH < 400) return DeviceType.MEDIUM;
  if (SCREEN_WIDTH < 768) return DeviceType.LARGE;
  return DeviceType.TABLET;
};

// Kullanım örnekleri:
/*
import { StyleSheet } from 'react-native';
import { wp, hp, fp, rp, getScreenInfo, DeviceType, ScreenInfo } from './responsiveFunctions';

// Style objesi içinde kullanım
const styles = StyleSheet.create({
  container: {
    width: wp(300),        // 300px genişlik
    height: hp(200),       // 200px yükseklik
    padding: wp(20),       // 20px padding
    marginTop: hp(50),     // 50px margin top
  },
  text: {
    fontSize: fp(16),      // 16px font boyutu
    lineHeight: fp(24),    // 24px line height
  },
  button: {
    width: wp(150),
    height: hp(44),
    borderRadius: rp(8),   // Genel responsive
  }
});

// TypeScript ile tip güvenli kullanım
const screenInfo: ScreenInfo = getScreenInfo();
const deviceType: DeviceType = getDeviceType();

// Conditional styling
const getButtonSize = (): { width: number; height: number } => {
  switch (deviceType) {
    case DeviceType.SMALL:
      return { width: wp(120), height: hp(40) };
    case DeviceType.MEDIUM:
      return { width: wp(140), height: hp(44) };
    case DeviceType.LARGE:
      return { width: wp(160), height: hp(48) };
    case DeviceType.TABLET:
      return { width: wp(200), height: hp(52) };
    default:
      return { width: wp(150), height: hp(44) };
  }
};
*/
```
