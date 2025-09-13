Tamam TkMatE — **sınıflar (classes)** ile derinlemesine başlayalım. Aşağıda hem kavramsal açıklamalar hem de üretime yakın, kullanışlı örneklerle adım adım gidiyorum. Uzun olacak ama her parça pratikte işine yarayacak.

# 1) Temel sınıf (basic class)

```dart
class Person {
  String name = '';
  int age = 0;

  void introduce() {
    print('Merhaba, ben $name, $age yaşındayım.');
  }
}

void main() {
  var p = Person();
  p.name = 'TkMatE';
  p.age = 25;
  p.introduce();
}
```

- `class` anahtar kelimesi ile tanımlanır.
- Özellikler (fields) ve metodlar sınıf içinde yer alır.

---

# 2) Constructor (yapıcı) çeşitleri

### a) Varsayılan / positional constructor

```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);
}
```

### b) Named parametreli (daha okunaklı)

```dart
class Person {
  String name;
  int age;

  Person({required this.name, required this.age});
}
```

### c) Optional positional

```dart
class Person {
  String name;
  int? age;
  Person(this.name, [this.age]); // age opsiyonel
}
```

### d) Named constructor (farklı başlangıç yolları)

```dart
class Person {
  String name;
  int age;
  Person(this.name, this.age);

  Person.guest() : name = 'Misafir', age = 0;
}
```

### e) Initializer list (final alanları başlatmak için)

```dart
class Point {
  final int x;
  final int y;
  Point.fromMap(Map m) : x = m['x'] ?? 0, y = m['y'] ?? 0;
}
```

---

# 3) `const` ve `final` alanlara sahip constructor'lar

- `const` constructor: tüm alanlar `final` olmalı ve constructor `const` olmalı.

```dart
class ImmutablePoint {
  final int x, y;
  const ImmutablePoint(this.x, this.y);
}

const p = ImmutablePoint(1,2); // compile-time sabit
```

- `final` alanlar: constructor veya initializer ile bir kere atanır.

---

# 4) Factory konstruktörler

- Nesne yaratmayıp başka bir nesne/daha önceden oluşturulmuş örneği döndürebilir.

```dart
class Logger {
  static final Map<String, Logger> _cache = {};
  final String name;
  factory Logger(String name) {
    return _cache[name] ??= Logger._internal(name);
  }
  Logger._internal(this.name);
}
```

- Singleton, caching veya JSON’dan nesne yaratma için sık kullanılır.

---

# 5) Getter / Setter ve kapsülleme (encapsulation)

```dart
class BankAccount {
  double _balance = 0; // private alan (library scope)
  double get balance => _balance;
  set balance(double value) {
    if (value >= 0) _balance = value;
  }
}
```

- `_` ile başlayan isimler sadece aynı kütüphane içinde görünür (library-private).

---

# 6) `late` anahtar kelimesi

- Sonradan (ama null olmadan) başlatılması garanti edilen alanlar için.

```dart
class Config {
  late final String apiKey;
  void init(String key) => apiKey = key;
}
```

- `late` atanmadan okunursa `LateInitializationError` fırlatır.

---

# 7) Static üyeler

- Sınıfa bağlı, nesneye bağlı olmayan değişken/metod.

```dart
class MathUtil {
  static const double pi = 3.141592;
  static double circleArea(double r) => pi * r * r;
}
```

---

# 8) Inheritance (kalıtım) ve `super`

```dart
class Animal {
  void speak() => print('...');
}

class Dog extends Animal {
  @override
  void speak() => print('Hav hav');
}
```

- `extends` ile miras alırsın. `@override` kullanmak iyi pratiktir.
- `super(...)` ile üst sınıf constructor’ını çağırırsın.

```dart
class Person {
  String name;
  Person(this.name);
}
class Employee extends Person {
  int id;
  Employee(String name, this.id) : super(name);
}
```

---

# 9) Abstract sınıflar & interface (implements)

- Abstract sınıf içerisinde soyut (gövdesiz) metodlar tanımlanır.

```dart
abstract class Shape {
  double area();
}

class Circle implements Shape {
  final double r;
  Circle(this.r);
  @override
  double area() => 3.14 * r * r;
}
```

- `implements` ile tam bir interface olarak davranırsın (tüm metodları override etmelisin).

---

# 10) Mixins

- Tekrarlı davranışları sınıflara eklemek için kullanılır.

```dart
mixin Logger {
  void log(String msg) => print('[LOG] $msg');
}

class Service with Logger {
  void doSomething() => log('yapıldı');
}
```

---

# 11) Generics (generic sınıflar)

```dart
class Box<T> {
  T value;
  Box(this.value);
}

var intBox = Box<int>(5);
```

- Tekrar kullanılabilir, tip güvenli sınıflar için.

---

# 12) Operator overloading (operatörleri özelleştirme)

```dart
class Point {
  final int x, y;
  Point(this.x, this.y);
  Point operator +(Point other) => Point(x + other.x, y + other.y);
}
```

- `operator` anahtar kelimesiyle toplama, eşitleme, index operatörleri vs. özelleştirilebilir. 

---

# 13) `toString`, `==` ve `hashCode` override (eşitlik ve debugging)

```dart
class Person {
  final String name;
  final int age;
  Person(this.name, this.age);

  @override
  String toString() => 'Person($name, $age)';

  @override
  bool operator ==(Object other) =>
      identical(this, other) ||
      other is Person && other.name == name && other.age == age;

  @override
  int get hashCode => Object.hash(name, age);
}
```

- `==` ve `hashCode` doğru override edilmezse koleksiyonlarda sorun olur.

---

# 14) Immutable pattern ve `copyWith`

- Immutable veri modellerinde `copyWith` sıklıkla kullanılır:

```dart
class User {
  final String name;
  final int age;
  const User({required this.name, required this.age});

  User copyWith({String? name, int? age}) =>
      User(name: name ?? this.name, age: age ?? this.age);
}
```

---

# 15) Örnek: JSON serileştirme ile pratik sınıf

```dart
class Person {
  final String name;
  final int age;
  Person({required this.name, required this.age});

  factory Person.fromJson(Map<String, dynamic> json) =>
      Person(name: json['name'], age: json['age']);

  Map<String, dynamic> toJson() => {'name': name, 'age': age};
}
```

---

# 16) İyi uygulama (best practices) & yaygın hatalar

- Alanları gerektiğinde `final` yap: değişmezliği garantile.
- `const` constructor varsa nesneleri compile-time sabit yap; performans avantajı var.
- `_private` üyeleri sınıf dışına sızmaz — fakat aynı kütüphane içinden erişilir (dosya bazlı değil, library bazlı).
- `late` kullanırken dikkatli ol (atama garantilenmeli).
- `==` ve `hashCode` uyumlu olmalı.
- JSON parse gibi tekrarlayan kod için `json_serializable` gibi paketler kullan (ileride istersen anlatırım).

---

# 17) Hızlı özet / yol haritası

1. Basit class → özellikler + metodlar
    
2. Constructor türleri → positional, named, named constructors, initializer list
    
3. `final` / `const` ile immutable yapılar
    
4. Getter/setter ile encapsulation
    
5. Static, late, private `_`
    
6. Inheritance, `super`, `@override`
    
7. Abstract / implements / mixin
    
8. Generics, operator overloading, factory constructors
    
9. Equality (`==` + `hashCode`), `toString`, `copyWith`
    
10. JSON serileştirme ve pratik pattern’ler
    

---

TkMatE, istersen şimdi sıra ile bu alt konulardan birine örnek kodla çok daha derin inelim (ör. **`const` constructor kuralları ve immutable modeller** mi, yoksa **factory + singleton pattern** mi, ya da **== / hashCode** nasıl test edilir). Hangi alt konu ile derinleşelim? Ben seçmezsen ben **const/final/immutable + copyWith + eşitlik** kombinasyonuyla devam ederim — bunlar genelde en çok kafa karıştıran kısımlar.