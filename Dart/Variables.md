
Değişkenler, **veriyi saklamak** için kullanılan isimlendirilmiş alanlardır.  
Dart, **tip güvenli** bir dildir, yani değişken tipi derleme zamanında kontrol edilir.

---

## 2. Değişken Tanımlama

### a) Tip Belirterek

```dart
int age = 25;           // Tam sayı
double height = 1.75;   // Ondalıklı sayı
String name = "TkMatE"; // Metin
bool isStudent = true;  // Mantıksal değer
```

### b) `var` ile

- Tip otomatik çıkarılır.

```dart
var city = "Istanbul";  // Dart bunu String olarak algılar
var score = 95;         // Dart bunu int olarak algılar
```

### c) `dynamic` ile

- Tip değişebilir.

```dart
dynamic value = 10;
value = "Merhaba";  // Hata vermez, tip değişti
```

**Not:** Mümkünse `dynamic` yerine `var` veya tip belirtmek daha güvenlidir.

---

## 3. Sabitler ve Final

### a) `final`

- Bir kez atanabilir, sonradan değiştirilemez.

```dart
final name = "TkMatE";
// name = "Ahmet";  // Hata verir
```

### b) `const`

- Derleme zamanında sabittir, program boyunca değişmez.

```dart
const pi = 3.14;
// pi = 3.1415;  // Hata verir
```

### Fark:

- `final` → runtime (çalışma zamanı) sabiti
- `const` → compile-time (derleme zamanı) sabiti

---

## 4. Nullable ve Null Safety

- Dart 2.12+ sürümünde **Null Safety** var.
- Bir değişken `null` olamaz, eğer `?` eklenirse null olabilir.

```dart
String? middleName;  // null olabilir
String lastName = "Arpacı"; // null olamaz
```

### Null-aware operatörler

```dart
String? nickname;
print(nickname ?? "Takma isim yok"); // nickname null ise default yazı
```

---

## 5. Tip Dönüşümleri

```dart
int a = 10;
double b = a.toDouble();  // int → double
String c = a.toString();  // int → String

String s = "123";
int n = int.parse(s);     // String → int
```

---

## 6. Değişken İsimlendirme Kuralları

- Harf veya `_` ile başlamalı, rakamla başlayamaz: `_age`, `name1`
- Boşluk veya özel karakter kullanılamaz
- camelCase kullanımı yaygın: `firstName`, `totalScore`
- Dart anahtar kelimeleri değişken adı olamaz: `class`, `void` vb.

---

## 7. Örnek Kod

```dart
void main() {
  int age = 20;
  var city = "Istanbul";
  final country = "Turkey";
  const pi = 3.14;

  String? middleName; // Null olabilir
  middleName = "Furkan";

  print("Yaş: $age");
  print("Şehir: $city");
  print("Ülke: $country");
  print("Pi: $pi");
  print("Orta ad: ${middleName ?? 'Yok'}");
}
```
