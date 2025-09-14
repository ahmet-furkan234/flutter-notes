
- Mixins, bir sınıfa **başka sınıfların özelliklerini (method, field)** **çoklu kalıtım** gibi eklemeyi sağlar.
- `extends` ile sadece **tek bir sınıftan miras alabilirsin**, ama **mixin ile birden fazla kaynaktan özellik çekebilirsin**.
- `mixin` anahtar kelimesiyle tanımlanır.

---

## 🔹 1. Basit Mixin Tanımı

```dart
mixin Flyable {
  void fly() => print("Uçuyorum!");
}

mixin Swimmable {
  void swim() => print("Yüzüyorum!");
}

class Bird with Flyable, Swimmable {}

void main() {
  var bird = Bird();
  bird.fly();   // Uçuyorum!
  bird.swim();  // Yüzüyorum!
}
```

📌 Açıklama:

- `Flyable` ve `Swimmable` mixin.
- `Bird` → `with` ile her ikisini de alıyor
- Çoklu kalıtım gibi → birden fazla davranış ekleyebiliyorsun.

---

## 🔹 2. Mixin ile `class` Farkı

- `class` → `extends` ile miras alınır → **sadece bir tane olabilir**.
- `mixin` → `with` ile dahil edilir → **birden fazla olabilir**.
- Mixin’in **constructor’ı olmaz**.

---

## 🔹 3. Abstract Class + Mixin

Mixinler, normal metodlar da içerebilir ama genelde **davranış eklemek için** kullanılır.

```dart
mixin Logger {
  void log(String message) {
    print("LOG: $message");
  }
}

abstract class Device {
  void start();
}

class Printer extends Device with Logger {
  @override
  void start() {
    log("Printer başlatılıyor...");
  }
}
```

📌 Burada `Printer`, hem **Device’i miras alıyor** hem de **Logger mixin’i ekliyor**.

---

## 🔹 4. Mixin Restrictions (`on` Anahtar Kelimesi)

Mixin’lerin sadece belirli sınıflara uygulanmasını istiyorsan → `on` kullanılır.

```dart
class Animal {
  void breathe() => print("Nefes alıyor...");
}

mixin Walker on Animal {
  void walk() => print("Yürüyor...");
}

class Dog extends Animal with Walker {}

class Car with Walker {} // ❌ HATA! Çünkü Walker sadece Animal üzerinde çalışabilir
```

📌 `Walker` mixin’i sadece `Animal`’dan türeyen sınıflarda kullanılabilir.

---

## 🔹 5. Çoklu Mixin Kullanımı

```dart
mixin A {
  void foo() => print("A");
}

mixin B {
  void foo() => print("B");
}

class C with A, B {}

void main() {
  var c = C();
  c.foo(); // B (son mixin kazanır)
}
```

📌 **Mixin sırası önemli** → aynı metod varsa en sondaki kazanır.

---

## 🔹 6. Özet

- `mixin` → başka sınıflara özellik eklemek için kullanılır.
- `with` anahtar kelimesiyle eklenir.
- Çoklu kalıtımı simüle eder.
- Constructor içeremez.
- `on` ile sınırlama getirilebilir.
- Aynı metod birden fazla mixin’de varsa **son eklenen kazanır**.


