[[_ Kotlin bez tajemnic]]

------------

[[3.1. Fragments]]
[[3.2. View Models]]
[[3.3. View Binding]]


-----------------
# Android Studio 
- `File>Settings>Plugin`:
	- rainbow brackets
	- nyan progress bar


# Activity and lifecycle

- `: AppCompatActivity()` dziedziczenie po tej klasie sprawia, że dana klasa jest `activity`
- definicja startowej aktywności  oraz wszystkie pozostałe aktywności w `AndroidManifest`

```xml
<activity  
    android:name=".MainActivity"  
    android:exported="true"  
    android:screenOrientation="portrait">  
    <intent-filter>  
        <action android:name="android.intent.action.MAIN" />  
  
        <category android:name="android.intent.category.LAUNCHER" />  
    </intent-filter>  
</activity>
```

- aktywności należy dzielić na fragmenty, a nie tworzyć nowe aktywności
- 



------
# View models

## **MVVM**
- widok/*view* to w naszym przypadku fragment i aktywność:
	- odpowiadają za wyświetlanie treści
	- odpowiadają za odbieranie akcji użytkownika
	- jest połączony z *view model*
- *view model* :
	- tu zachodzi cała logika biznesowa:
		- np. pobieranie informacji z modelu
		- np. zapisywanie zmodyfikowanych danych do repozytorium



[[3.1. Fragments]]
[[3.2. View Models]]
[[3.3. View Binding]]


[[4. Widoki]]







