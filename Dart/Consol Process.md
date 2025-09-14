
Dart’ta konsol uygulamaları yazarken en sık kullanılan kütüphane:

```dart
import 'dart:io';
```

Bu sayede **kullanıcıdan giriş alma (input)** ve **ekrana yazdırma (output)** işlemleri yapılır.

---

## 🔹 1. Ekrana Yazı Yazdırma (Output)

```dart
void main() {
  print("Merhaba Dart!");       // Satır sonunda otomatik \n (alt satıra geçer)
  stdout.write("Merhaba ");     // Alt satıra geçmez
  stdout.write("TkMatE\n");     // Manuel satır sonu
}
```

📌 `print` → satır sonu ekler.  
📌 `stdout.write` → satır sonu eklemez.

---

## 🔹 2. Kullanıcıdan Giriş Alma (Input)

```dart
import 'dart:io';

void main() {
  stdout.write("Adınızı girin: ");
  String? name = stdin.readLineSync(); // null dönebilir

  print("Merhaba, $name!");
}
```

📌 `stdin.readLineSync()` → String döner (nullable).  
📌 `stdout.write()` → ekrana mesaj basar ama satır atlamaz.

---

## 🔹 3. String → Sayıya Dönüştürme

Konsoldan alınan veriler **string** tipindedir.  
Sayısal işlem yapmak için dönüştürmek gerekir:

```dart
import 'dart:io';

void main() {
  stdout.write("Bir sayı girin: ");
  int number = int.parse(stdin.readLineSync()!);

  stdout.write("Bir ondalık sayı girin: ");
  double decimal = double.parse(stdin.readLineSync()!);

  print("Tam sayı: $number, Ondalık: $decimal");
}
```

📌 `!` → null safety operatörü (input’un boş gelmeyeceğini garanti ediyoruz).

---

## 🔹 4. Try-Catch ile Hatalı Giriş Kontrolü

```dart
import 'dart:io';

void main() {
  stdout.write("Bir sayı girin: ");
  try {
    int number = int.parse(stdin.readLineSync()!);
    print("Sayı: $number");
  } catch (e) {
    print("Geçersiz giriş yaptınız! 🚨");
  }
}
```

📌 Kullanıcı yanlış giriş yaparsa (örneğin "abc"), program çökmek yerine hata yakalar.

---

## 🔹 5. Konsol Temizleme (Platform Bağımlı)

Konsolu temizlemek için:

```dart
import 'dart:io';

void clearConsole() {
  if (Platform.isWindows) {
    // Windows için
    stdout.write("\x1B[2J\x1B[0;0H");
  } else {
    // Linux / Mac için
    print("\x1B[2J\x1B[0;0H");
  }
}

void main() {
  print("Merhaba!");
  sleep(Duration(seconds: 2));
  clearConsole();
  print("Konsol temizlendi!");
}
```

📌 Çapraz platform çalışsın diye `Platform.isWindows` kontrolü yapılır.

---

## 🔹 6. Kullanıcıdan Menü Girişi Alma

Bu yapı neredeyse bütün mini projelerde işine yarayacak 👇

```dart
import 'dart:io';

void main() {
  while (true) {
    print("\n=== Menü ===");
    print("1. Merhaba de");
    print("2. Çıkış");
    stdout.write("Seçiminizi yapın: ");

    String? choice = stdin.readLineSync();

    switch (choice) {
      case "1":
        print("Merhaba TkMatE 👋");
        break;
      case "2":
        print("Çıkış yapılıyor...");
        return; // programdan çık
      default:
        print("Geçersiz seçim!");
    }
  }
}
```

📌 Menü tabanlı konsol uygulamaları → **ToDo, ATM, Library System** gibi projelerde kullanılır.

---

✅ Özet:

- `print()` → satır atlar, hızlı kullanım.
- `stdout.write()` → satır atlamaz, kullanıcı girişi için uygun.
- `stdin.readLineSync()` → string input alır.
- `int.parse()` / `double.parse()` → sayıya çevirir.
- `try-catch` → hatalı girişleri yönetir.
- Menü yapısı → konsol projelerinin temel iskeleti.
