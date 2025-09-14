
# 🟦 Büyük Örnek: Hayvanlar Dünyası

```dart
// 1️⃣ Abstract Class → Şablon (ne yapılmalı)
abstract class Animal {
  String name;
  Animal(this.name);

  void makeSound(); // her hayvan ses çıkarmak zorunda
}

// 2️⃣ Mixins → Hazır davranış (nasıl yapılacağı belli)
mixin Walker {
  void walk() => print("Yürüyorum...");
}

mixin Swimmer {
  void swim() => print("Yüzüyorum...");
}

mixin Flyer {
  void fly() => print("Uçuyorum...");
}

// 3️⃣ Normal Class → Gerçek hayvanlar
class Dog extends Animal with Walker {
  Dog(String name) : super(name);

  @override
  void makeSound() => print("$name: Hav hav!");
}

class Duck extends Animal with Walker, Swimmer, Flyer {
  Duck(String name) : super(name);

  @override
  void makeSound() => print("$name: Vak vak!");
}

class Fish extends Animal with Swimmer {
  Fish(String name) : super(name);

  @override
  void makeSound() => print("$name: Blup blup!");
}

// 4️⃣ Kullanım
void main() {
  Dog d = Dog("Karabaş");
  d.makeSound(); // Hav hav!
  d.walk();      // Yürüyorum...

  Duck duck = Duck("Donald");
  duck.makeSound(); // Vak vak!
  duck.walk();      // Yürüyorum...
  duck.swim();      // Yüzüyorum...
  duck.fly();       // Uçuyorum...

  Fish f = Fish("Nemo");
  f.makeSound(); // Blup blup!
  f.swim();      // Yüzüyorum...
}
```

---

## 🔎 Burada olanlar

1. **Abstract class (Animal)** → “Her hayvan bir `makeSound()` yapmalı” diyerek **şablon** oluşturdu.
2. **Mixinler (Walker, Swimmer, Flyer)** → Yürümeyi, yüzmeyi, uçmayı **hazır davranış** olarak verdiler.
3. **Concrete class (Dog, Duck, Fish)** →
    - `Animal`’dan kalıtım aldı → `makeSound()`’ı **override etmek zorunda kaldı**.
    - `with` ile istediği mixin’leri ekledi (çoklu kalıtım gibi).

---

## 🟦 Sonuç

- **Abstract class**: “Ne yapılmalı?” (zorunlu kural → `makeSound`).
- **Mixin**: “Nasıl yapılacağı hazır” (`walk`, `swim`, `fly`).
- **Class**: “Gerçek nesne” (Dog, Duck, Fish).

📌 Yani hepsi farklı bir ihtiyacı karşılıyor.

- Abstract → iskelet
- Mixin → çoklu özellik
- Class → gerçek model
