
Kelime anlamı: **Poly → çok, morph → şekil**.  
Yani bir nesnenin **birden fazla farklı şekilde davranabilmesi**.

Dart’ta polymorphism genellikle **inheritance (kalıtım)** ve **interface/abstract class** ile ortaya çıkar.

---

## 🔹 1. Temel Mantık

Bir üst sınıf türünden referans, alt sınıf nesnesini gösterebilir.  
Çağrılan metod, nesnenin **gerçek tipine göre** çalışır.

```dart
class Animal {
  void makeSound() => print("Hayvan ses çıkarıyor");
}

class Dog extends Animal {
  @override
  void makeSound() => print("Köpek havlıyor");
}

class Cat extends Animal {
  @override
  void makeSound() => print("Kedi miyavlıyor");
}

void main() {
  Animal a1 = Dog(); // Animal tipinde, Dog nesnesi
  Animal a2 = Cat(); // Animal tipinde, Cat nesnesi

  a1.makeSound(); // Köpek havlıyor
  a2.makeSound(); // Kedi miyavlıyor
}
```

📌 Burada `a1` ve `a2` tip olarak **Animal** ama davranışları **Dog ve Cat**’e göre değişiyor. İşte polymorphism bu.

---

## 🔹 2. Abstract Class ile Polymorphism

Abstract class ile alt sınıflara **zorunlu davranış** tanımlarsın, polymorphism ile hangi sınıfın davranışı çalışacağını bilmeden çağırabilirsin.

```dart
abstract class Shape {
  double area();
}

class Circle extends Shape {
  double r;
  Circle(this.r);

  @override
  double area() => 3.14 * r * r;
}

class Rectangle extends Shape {
  double w, h;
  Rectangle(this.w, this.h);

  @override
  double area() => w * h;
}

void main() {
  List<Shape> shapes = [
    Circle(5),
    Rectangle(4, 6),
  ];

  for (var shape in shapes) {
    print("Alan: ${shape.area()}");
  }
}
```

📌 Liste **Shape** tipinde ama her eleman farklı şekil.  
Metod çağırıldığında doğru implementasyon çalışıyor → polymorphism.

---

## 🔹 3. Interface (implements) ile Polymorphism

```dart
abstract class Playable {
  void play();
}

class Guitar implements Playable {
  @override
  void play() => print("Gitar çalıyor");
}

class Piano implements Playable {
  @override
  void play() => print("Piyano çalıyor");
}

void main() {
  List<Playable> instruments = [
    Guitar(),
    Piano(),
  ];

  for (var inst in instruments) {
    inst.play();
  }
}
```

📌 `Playable` tipinden liste tuttuk → polymorphism sayesinde hangi çalgı olursa olsun `play()` çalışıyor.

---

## 🔹 4. Runtime Polymorphism (Override)

Alt sınıf, üst sınıftaki metodu **override** ederse runtime’da gerçek nesnenin metodu çalışır.

## 🔹 5. Compile-time Polymorphism (Overloading → Dart’ta yok)

C# veya Java’da aynı isimli metotları farklı parametrelerle tanımlayabilirsin (method overloading).  
👉 Dart’ta **direct method overloading yok**. Onun yerine:

- **Optional positional parameters** `[ ]`
- **Named parameters** `{ }`  
    kullanılır. (bunu seninle daha önce işlemiştik 😉)

---

## 🟦 Özet

- **Polymorphism** → aynı referans tipinin farklı davranış gösterebilmesi.
- `extends` → miras alıp override ederek yapılır.
- `implements` → interface gibi, override zorunlu.
- Compile-time polymorphism Dart’ta yok, ama opsiyonel/named parametrelerle benzer işlev sağlanıyor.
