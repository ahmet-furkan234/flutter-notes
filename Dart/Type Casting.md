
Dart’ta tip dönüşümü (casting), bir değişkeni **farklı bir tipe dönüştürmek** veya **başka bir tipteymiş gibi kullanmak** anlamına gelir.  
İki ana başlıkta incelenir:

1. **Primitive (ilkel) tip dönüşümleri** → `int ↔ double ↔ String`
2. **Object casting (Nesne dönüşümü)** → `as`, `is`, `is!` operatörleri

---

## 🔹 1. Primitive Tip Dönüşümleri

### ✅ int ↔ double

```dart
void main() {
  int a = 10;
  double b = a.toDouble(); // int → double
  print(b); // 10.0

  double c = 15.7;
  int d = c.toInt(); // double → int
  print(d); // 15 (ondalık kısmı siler)
}
```

---

### ✅ String ↔ int / double

```dart
void main() {
  // String → int
  String s1 = "42";
  int n1 = int.parse(s1);
  print(n1 + 8); // 50

  // String → double
  String s2 = "3.14";
  double n2 = double.parse(s2);
  print(n2 * 2); // 6.28

  // int → String
  int num = 100;
  String str1 = num.toString();
  print(str1); // "100"

  // double → String
  double pi = 3.14159;
  String str2 = pi.toStringAsFixed(2); // 2 ondalık basamak
  print(str2); // "3.14"
}
```

📌 `int.parse()` ve `double.parse()` hatalı girişte **FormatException** fırlatır → `try-catch` ile yakalamak gerekir.

---

## 🔹 2. Object Casting (as, is, is!)

Dart nesne tabanlı olduğundan bazen **inheritance** ve **polymorphism** durumlarında tip dönüşümü gerekir.

### ✅ `is` Operatörü (Tip Kontrolü)

```dart
class Animal {}
class Dog extends Animal {}
class Cat extends Animal {}

void main() {
  Animal a = Dog();

  if (a is Dog) {
    print("Bu bir köpek!");
  } else if (a is Cat) {
    print("Bu bir kedi!");
  }
}
```

📌 `is` → değişkenin belirtilen tipten olup olmadığını kontrol eder.

---

### ✅ `as` Operatörü (Explicit Cast)

```dart
class Animal {
  void makeSound() => print("Bir ses çıkarıyor...");
}

class Dog extends Animal {
  void bark() => print("Hav hav!");
}

void main() {
  Animal a = Dog();

  // a değişkeni aslında Dog, o yüzden cast edebiliriz
  (a as Dog).bark(); // Hav hav!
}
```

📌 `as` → tip dönüşümünü **zorla yapar**. Eğer yanlış tipse → `TypeError` fırlatır.

---

### ✅ `is!` Operatörü (Değilse Kontrolü)

```dart
void main() {
  Object value = "Merhaba";

  if (value is! int) {
    print("Bu bir int değil!");
  }
}
```

---

## 🔹 3. Upcasting & Downcasting

- **Upcasting (Yukarı dönüşüm)**: Alt sınıf → üst sınıf
- **Downcasting (Aşağı dönüşüm)**: Üst sınıf → alt sınıf

```dart
class Animal {
  void sound() => print("Hayvan ses çıkarıyor");
}

class Dog extends Animal {
  void bark() => print("Köpek havlıyor");
}

void main() {
  // Upcasting (otomatik)
  Dog dog = Dog();
  Animal a = dog; // Dog → Animal
  a.sound();

  // Downcasting (manuel, 'as' kullanılır)
  Animal b = Dog();
  (b as Dog).bark(); // cast edilmezse bark() görünmez
}
```

---

## 🔹 4. Null Safety ile Casting

```dart
void main() {
  Object? data = "Hello";

  String str = data as String;  // güvenli çünkü String
  print(str.toUpperCase());

  Object? number = 123;
  String? str2 = number as String?; // yanlış cast → hata
}
```

📌 Dart’ta yanlış casting yapıldığında **TypeError** alırsın.

---

## 🔹 5. Özet

- **Primitive casting** → `int`, `double`, `String` arası dönüşüm
- **is** → tip kontrolü
- **as** → tip dönüşümü (hatalıysa exception fırlatır)
- **is!** → belirtilen tip değilse kontrol
- **Upcasting** → otomatik (alt → üst)
- **Downcasting** → manuel (üst → alt, `as` ile)
