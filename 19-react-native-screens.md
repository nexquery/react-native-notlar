## Açıklama
react-native-screens çökmelerine karşı alınması gereken bir önlem;

## Kotlin
`android/app/src/main/java/<paket adı>/MainActivity.kt`
```kt
import android.os.Bundle;
import com.swmansion.rnscreens.fragment.restoration.RNScreensFragmentFactory;

class MainActivity: ReactActivity() {

    //...code

    //react-native-screens override
    override fun onCreate(savedInstanceState: Bundle?) {
      supportFragmentManager.fragmentFactory = RNScreensFragmentFactory()
      super.onCreate(savedInstanceState);
    }
}
```

## Java
`android/app/src/main/java/<paket adı>/MainActivity.java`
```java
import android.os.Bundle;
import com.swmansion.rnscreens.fragment.restoration.RNScreensFragmentFactory;

public class MainActivity extends ReactActivity {

    //...code

    //react-native-screens override
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        getSupportFragmentManager().setFragmentFactory(new RNScreensFragmentFactory());
        super.onCreate(savedInstanceState);
    }

    public static class MainActivityDelegate extends ReactActivityDelegate {
        //...code
    }
}
```
