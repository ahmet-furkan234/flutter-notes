
## 1. **final ile immutability**

- `final` değişken **sadece bir kez atanabilir**.    
- Ancak `final` ile işaretlenmiş **koleksiyonların içeriği değiştirilebilir** (list, map, set).

```dart
void main() {
  final List<int> numbers = [1, 2, 3];
  
  numbers.add(4); // ✅ içerik değiştirilebilir
  print(numbers); // [1, 2, 3, 4]

  // numbers = [5, 6, 7]; ❌ yeniden atanamaz
}
```

📌 `final` → referans sabittir, ama içerik değişebilir.

---

## 2. **const ile immutability**

- `const` → hem referans **hem de içeriği** sabittir.    
- Compile-time sabit olması gerekir.

```dart
void main() {
  const List<int> numbers = [1, 2, 3];
  
  // numbers.add(4); ❌ hata! const liste değiştirilemez
  print(numbers); // [1, 2, 3]
}
```

📌 `const` → tamamen değiştirilemez (deep immutability).

---

## 3. **Class İçinde immutable yapılar**

Eğer sınıfın `final` alanları varsa, nesne oluşturulduktan sonra değiştirilemez.

```dart
class User {
  final String name;
  final int age;

  User(this.name, this.age);
}

void main() {
  var u = User("Ahmet", 25);

  print("${u.name}, ${u.age}");
  // u.age = 30; ❌ final alan değiştirilemez
}
```

---

## 4. **const Constructor ile Immutable Class**

Eğer bir sınıfın tüm alanları `final` ise ve constructor `const` tanımlandıysa → compile-time’da immutable nesneler üretilebilir.

```dart
class Point {
  final int x;
  final int y;

  const Point(this.x, this.y);
}

void main() {
  const p1 = Point(1, 2);
  const p2 = Point(1, 2);

  print(identical(p1, p2)); // true → aynı nesne
}
```

📌 `const` constructor sayesinde nesneler hafızada paylaşılır → performans artışı.

---

## 5. **Immutable Koleksiyonlar**

- `const` koleksiyonlar → içeriği değiştirilemez.

```dart
void main() {
  const List<String> fruits = ["apple", "banana", "cherry"];
  // fruits.add("orange"); ❌ hata

  const Map<String, int> scores = {"A": 100, "B": 90};
  // scores["C"] = 80; ❌ hata
}
```

---

## 6. **Factory ile Immutable Nesne Paylaşımı**

Aynı immutable nesneyi tekrar tekrar oluşturmamak için `factory` constructor kullanılabilir.

```dart
class Logger {
  final String name;
  static final Map<String, Logger> _cache = {};

  factory Logger(String name) {
    return _cache.putIfAbsent(name, () => Logger._internal(name));
  }

  Logger._internal(this.name);
}

void main() {
  var l1 = Logger("UI");
  var l2 = Logger("UI");

  print(identical(l1, l2)); // true → aynı nesne
}
```

---

# 📌 Özet

- **`final`** → referans sabit, içerik değişebilir.
- **`const`** → hem referans hem içerik sabit (tam immutable).
- **final + const constructor** → immutable class.
- **factory + cache** → aynı immutable nesneyi paylaşma.
