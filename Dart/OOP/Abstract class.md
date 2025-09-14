
Bir **abstract class**, direkt olarak **nesne oluşturulamaz** ama kendisinden türetilen sınıflara **bir şablon** sağlar.  
Yani “bu metodları yazmalısın” gibi **zorunluluk** getirir.

---

## 🟢 Tanım

- `abstract` anahtar kelimesi ile tanımlanır.
- İçinde hem **normal metodlar** hem de **abstract metodlar** (gövdesiz metodlar) olabilir.
- `abstract` metod yazarsan, **alt sınıflar onu override etmek zorundadır**.

---

## 🟦 Örnek 1: Basit Abstract Class

```dart
abstract class Animal {
  void sound(); // abstract method (gövdesiz)
  
  void sleep() {
    print("Hayvan uyuyor");
  }
}

class Dog extends Animal {
  @override
  void sound() {
    print("Köpek havlıyor");
  }
}

class Cat extends Animal {
  @override
  void sound() {
    print("Kedi miyavlıyor");
  }
}

void main() {
  // Animal a = Animal(); // HATA ❌ (abstract class new'lenemez)

  Dog d = Dog();
  d.sound();  // Köpek havlıyor
  d.sleep();  // Hayvan uyuyor

  Cat c = Cat();
  c.sound();  // Kedi miyavlıyor
  c.sleep();  // Hayvan uyuyor
}
```

---

## 🟦 Örnek 2: Zorunlu Methodlar

```dart
abstract class Shape {
  double area();   // alan hesaplama (abstract)
  double perimeter(); // çevre hesaplama (abstract)
}

class Rectangle extends Shape {
  double width, height;
  Rectangle(this.width, this.height);

  @override
  double area() => width * height;

  @override
  double perimeter() => 2 * (width + height);
}

class Circle extends Shape {
  double radius;
  Circle(this.radius);

  @override
  double area() => 3.14 * radius * radius;

  @override
  double perimeter() => 2 * 3.14 * radius;
}

void main() {
  Shape rect = Rectangle(5, 10);
  print("Dikdörtgen Alanı: ${rect.area()}");       // 50
  print("Dikdörtgen Çevresi: ${rect.perimeter()}"); // 30

  Shape circle = Circle(3);
  print("Daire Alanı: ${circle.area()}");           // 28.26
  print("Daire Çevresi: ${circle.perimeter()}");    // 18.84
}
```

---

## 🟦 Örnek 3: Interface gibi Kullanım

Dart’ta **interface yok** → onun yerine **abstract class** kullanılabilir.  
Birden fazla abstract class davranışını almak için `implements` kullanılır.

```dart
abstract class Flyable {
  void fly();
}

abstract class Swimmable {
  void swim();
}

class Duck implements Flyable, Swimmable {
  @override
  void fly() {
    print("Ördek uçuyor");
  }

  @override
  void swim() {
    print("Ördek yüzüyor");
  }
}

void main() {
  Duck d = Duck();
  d.fly();
  d.swim();
}
```

📌 Burada `Duck`, hem **Flyable** hem **Swimmable** metodlarını **override etmek zorunda**.

---

## 🟦 Özet

- `abstract class` → new’lenemez.
- İçinde **abstract metod** (gövdesiz) ve normal metod olabilir.
- Alt sınıflar abstract metodları **override etmek zorunda**.
- Dart’ta interface olmadığı için abstract class **interface gibi** kullanılabilir (`implements`).
