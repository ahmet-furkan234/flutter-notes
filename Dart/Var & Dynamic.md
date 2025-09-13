
## 1. **`var`**

- Tip **otomatik çıkarılır** (type inference)
- Bir kez değer atandıktan sonra tipi **sabitlenir**, değiştirilemez

```dart
void main() {
  var name = "TkMatE";  // Dart bunu String olarak algılar
  print(name);

  // name = 123; // HATA! Tip değiştirilemez
}
```

- Avantajları:
    - Kod kısa ve temiz olur
    - Tip güvenliği sağlar
- Dezavantajları:
    - Başlangıçta değer ataması **zorunludur**, aksi halde derleme hatası verir:

```dart
var age; // HATA! Başlangıçta değer atamalısın
```

---

## 2. **`dynamic`**

- Tip kontrolü **çalışma zamanında yapılır**
- Her türlü veri atanabilir, tip değişebilir

```dart
void main() {
  dynamic value = 10;       // int
  print(value);

  value = "Merhaba";        // String
  print(value);

  value = true;             // bool
  print(value);
}
```

- Avantajları:
    - Esnek kullanım
    - Tip bilinmediğinde veya farklı tipler atanacaksa kullanışlı    
- Dezavantajları:
    - Tip güvenliği yok, runtime hataları oluşabilir
    - `var` kadar güvenli değil

---

## 3. **Karşılaştırma Tablosu**

|Özellik|`var`|`dynamic`|
|---|---|---|
|Tip çıkarımı|Derleme zamanında|Çalışma zamanında|
|Tip değişebilir|Hayır|Evet|
|Başlangıçta değer|Zorunlu|Opsiyonel|
|Tip güvenliği|Var|Yok|
|Örnek kullanım|`var name = "TkMatE";`|`dynamic value = 10;`|

---

## 4. **Örnek Kod**

```dart
void main() {
  var city = "Istanbul";
  // city = 123; // HATA!

  dynamic info = "Hello";
  info = 42;       // HATA vermez
  info = true;     // HATA vermez

  print("var city: $city");
  print("dynamic info: $info");
}
```

---

### ✅ Özet

- `var` → tip çıkarılır, **sabit tip**, güvenli
- `dynamic` → tip değişebilir, **esnek ama riskli**
