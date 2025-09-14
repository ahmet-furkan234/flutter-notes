
Dart’ta **ayrı bir `interface` anahtar kelimesi yok** ✅  
Ama **her class otomatik olarak bir interface gibi kullanılabilir**.

Yani Dart’ta:

- Java / C# → `interface` var
- Dart → `class` veya `abstract class` → `implements` ile interface gibi kullanılır

---

## 🔹 1. Normal Class'ı Interface gibi Kullanma

```dart
class Printer {
  void printData(String data) {
    print("Yazdırılıyor: $data");
  }
}

class Scanner {
  void scan() {
    print("Tarama yapılıyor...");
  }
}

// Interface gibi implements
class MultiFunctionMachine implements Printer, Scanner {
  @override
  void printData(String data) {
    print("MFM Yazdırıyor: $data");
  }

  @override
  void scan() {
    print("MFM Tarama yapıyor...");
  }
}

void main() {
  MultiFunctionMachine mfm = MultiFunctionMachine();
  mfm.printData("Belge.pdf");
  mfm.scan();
}
```

📌 Burada `Printer` ve `Scanner` aslında **normal class** ama `implements` ile interface gibi kullanıyoruz.  
MultiFunctionMachine bunların **tamamını override etmek zorunda**.

---

## 🔹 2. Abstract Class ile Interface Kullanımı

```dart
abstract class Flyable {
  void fly();
}

abstract class Swimmable {
  void swim();
}

class Duck implements Flyable, Swimmable {
  @override
  void fly() => print("Ördek uçuyor");

  @override
  void swim() => print("Ördek yüzüyor");
}
```

📌 Eğer class `implements` ile kullanılırsa → **tüm metodlar override edilmek zorunda**.  
Ama `extends` (kalıtım) ile kullanılınca → override zorunlu değil (sadece gerekirse yapılır).

---

## 🔹 3. Özet

- Dart’ta **ayrı bir `interface` yapısı yok**.
    
- Her class aslında **aynı zamanda bir interface**.
    
- `implements` ile interface gibi kullanılır.
    
- `extends` → kalıtım, davranış + metod alır.
    
- `implements` → sadece metod imzaları alınır, gövdeler yeniden yazılır.
    

---

👉 İstersen sırada **Mixins** var. Bu konu da `interface`’e çok yakın ama **çoklu kalıtımı** sağlar.  
Mixins’e geçelim mi?