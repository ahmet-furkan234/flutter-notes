
Kalıtım, bir sınıfın başka bir sınıfın **özelliklerini (fields)** ve **davranışlarını (methods)** miras almasını sağlar.  
Dart’ta `extends` anahtar kelimesiyle yapılır.

- **Superclass (Parent/Base Class)** → Miras alınan sınıf.
- **Subclass (Child/Derived Class)** → Miras alan sınıf.

👉 Avantajı: Kod tekrarını azaltır, yeniden kullanılabilirliği artırır.

---

## 🟣 Basit Örnek

```dart
// Üst sınıf (Parent Class)
class Animal {
  void eat() {
    print("Animal is eating");
  }
}

// Alt sınıf (Child Class)
class Dog extends Animal {
  void bark() {
    print("Dog is barking");
  }
}

void main() {
  var dog = Dog();
  dog.eat();   // Animal is eating (üst sınıftan miras)
  dog.bark();  // Dog is barking (kendi metodu)
}
```

✔️ `Dog` sınıfı `Animal` sınıfındaki `eat()` metodunu **otomatik miras aldı**.

---

## 🟣 Override (Üst Sınıf Metodunu Ezmek)

Alt sınıf, üst sınıfın metodunu **kendi ihtiyacına göre değiştirebilir**.  
Bunun için `@override` kullanılır.

```dart
class Animal {
  void makeSound() {
    print("Some animal sound");
  }
}

class Cat extends Animal {
  @override
  void makeSound() {
    print("Meow Meow");
  }
}

void main() {
  var cat = Cat();
  cat.makeSound(); // Meow Meow
}
```

---

## 🟣 super Anahtar Kelimesi

`super` → Üst sınıftaki **field’lara** ve **method’lara** erişmek için kullanılır.  
Özellikle constructor çağırırken önemlidir.

```dart
class Animal {
  String name;
  Animal(this.name);

  void display() {
    print("Animal name: $name");
  }
}

class Dog extends Animal {
  String breed;
  Dog(String name, this.breed) : super(name);

  @override
  void display() {
    super.display(); // üst sınıfın display() çağrıldı
    print("Dog breed: $breed");
  }
}

void main() {
  var dog = Dog("Karabas", "Kangal");
  dog.display();
  // Animal name: Karabas
  // Dog breed: Kangal
}
```

---

## 🟣 Çok Katmanlı Kalıtım (Multilevel Inheritance)

Dart’ta çok katmanlı kalıtım mümkündür (ama çoklu kalıtım **desteklenmez**).

```dart
class LivingBeing {
  void breathe() => print("Breathing...");
}

class Animal extends LivingBeing {
  void eat() => print("Eating...");
}

class Dog extends Animal {
  void bark() => print("Barking...");
}

void main() {
  var dog = Dog();
  dog.breathe(); // LivingBeing’den
  dog.eat();     // Animal’dan
  dog.bark();    // Dog’dan
}
```

---

## 🟣 Abstract Class ile Inheritance

Eğer bir sınıfın **tamamlanmamış metodları** varsa `abstract` yapılır.  
Alt sınıflar bu metodları `override` etmek **zorundadır**.

```dart
abstract class Animal {
  void makeSound(); // soyut (abstract) metod
}

class Dog extends Animal {
  @override
  void makeSound() {
    print("Hav Hav!");
  }
}

class Cat extends Animal {
  @override
  void makeSound() {
    print("Miyav!");
  }
}

void main() {
  var dog = Dog();
  dog.makeSound(); // Hav Hav!

  var cat = Cat();
  cat.makeSound(); // Miyav!
}
```

---

✅ Özet:

- `extends` → Kalıtım yapmak için.
- `@override` → Üst sınıf metodunu ezmek için.
- `super` → Üst sınıftaki field ve method’lara erişim.
- Çoklu kalıtım **yok** → Bunun yerine **mixin** kullanılır (ileride göreceğiz).

---

👉 TkMatE, istersek sıradaki konuya **abstract class’lar** ve **interface** detaylıca geçelim mi, yoksa inheritance içinde daha fazla özel kullanım örnekleri (private members, polymorphism vs.) inceleyelim mi?