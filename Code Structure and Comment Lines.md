
## 1. Dart Kod Yapısı

Dart kodları genellikle şu yapıda olur:

```dart
// Ana fonksiyon
void main() {
  // Kodlar buraya yazılır
  print("Merhaba Dart!");
}
```

### Açıklamalar:

- `void main()` → Dart uygulamalarının **başlangıç noktası**dır. Her Dart programı `main` fonksiyonundan başlar.
- `{ }` → Kod bloklarını belirler. Fonksiyon, sınıf veya kontrol yapılarının kapsamı `{ }` içinde yazılır.
- Satırlar `;` ile sonlandırılır. Dart, çoğu zaman otomatik sonlandırmayı desteklese de **her satırı `;` ile bitirmek iyi bir pratiktir.**

---

### Basit Örnek

```dart
void main() {
  int age = 20;        // yaş değişkeni
  String name = "TkMatE"; // isim değişkeni

  print("Merhaba $name, yaşın $age."); // Ekrana yazdırma
}
```

---

## 2. Yorum Satırları

Dart’ta üç tür yorum satırı vardır:

### a) Tek satır yorum

```dart
// Bu bir tek satır yorumdur
int number = 10; // Değişken ataması
```

### b) Çok satırlı yorum

```dart
/*
Bu birden fazla satırı kapsayan
yorum örneğidir.
*/
```

### c) Dokümantasyon yorumları

- Üçlü `/` veya `/** */` ile yazılır.
- Özellikle **sınıf, fonksiyon veya değişken açıklamaları** için kullanılır.
- IDE’ler ve DartDoc tarafından okunur.

```dart
/// Bu fonksiyon ekrana selam mesajı yazdırır
void greet(String name) {
  print("Merhaba $name!");
}

/**
 * Bu sınıf bir kişiyi temsil eder.
 * name ve age değişkenlerini tutar.
 */
class Person {
  String name;
  int age;
  
  Person(this.name, this.age);
}
```

---

### 3. İyi Pratikler

- Kod okunabilirliği için yorumları kısa ve net tut.
- Gereksiz yorumlardan kaçın; sadece **karmaşık veya önemli işlemleri** açıklamak yeterlidir.
- Dokümantasyon yorumları özellikle **Flutter ve paket geliştirme** için önemlidir.
