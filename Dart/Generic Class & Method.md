
# 🟦 Generics (Tür Parametreleri)

**Generics**, sınıfların, metodların veya koleksiyonların **tipini parametre olarak almasını sağlar**.

- Kod tekrarını azaltır.
- Tip güvenliğini artırır.
- Compile-time’da hataları yakalar.

Dart’ta generics, köşeli parantez `<T>` ile tanımlanır.

---

## 🔹 1. Generic Class Örneği

```dart
class Box<T> {
  T value;

  Box(this.value);

  void show() {
    print("Box içindeki değer: $value");
  }
}

void main() {
  Box<int> intBox = Box<int>(123);
  intBox.show(); // Box içindeki değer: 123

  Box<String> stringBox = Box<String>("Merhaba");
  stringBox.show(); // Box içindeki değer: Merhaba
}
```

📌 Açıklama:

- `T` → tip parametresi
- `Box<int>` → integer tipiyle kullanılıyor
- `Box<String>` → string tipiyle kullanılıyor
- Kod tekrarına gerek kalmadan farklı tipler için kullanılabilir

---

## 🔹 2. Generic Method Örneği

```dart
T getFirst<T>(List<T> items) {
  return items[0];
}

void main() {
  List<int> numbers = [1, 2, 3];
  List<String> words = ["Dart", "Flutter"];

  print(getFirst<int>(numbers)); // 1
  print(getFirst<String>(words)); // Dart
}
```

📌 Açıklama:

- `T` → metod seviyesinde tip parametresi
- List’in eleman tipine göre dönüş sağlar
- Compile-time’da tip kontrolü yapılır

---

## 🔹 3. Generic Constraint (Sınırlama)

Bazı durumlarda tip parametresinin **belirli bir sınıftan türemesini** isteyebilirsin.

```dart
class Person {
  void speak() => print("Konuşuyorum");
}

class Student extends Person {
  void study() => print("Çalışıyorum");
}

class School<T extends Person> {
  T member;

  School(this.member);

  void info() {
    member.speak();
  }
}

void main() {
  Student s = Student();
  School<Student> school = School<Student>(s);
  school.info(); // Konuşuyorum
}
```

📌 `<T extends Person>` → sadece `Person` veya türevleri kullanılabilir.

---

## 🔹 4. Generic List / Koleksiyonlar

Dart’ın koleksiyonları zaten **generic** olarak tanımlanır:

```dart
List<int> numbers = [1, 2, 3];
Map<String, int> ages = {"Ahmet": 25, "Ayşe": 30};
Set<String> names = {"TkMatE", "Dart"};
```

📌 Böylece yanlış tip atama compile-time’da yakalanır.

---

## 🔹 5. Özet

- Generics → kod tekrarını azaltır, tip güvenliği sağlar.
- `class MyClass<T> {}` → generic class
- `T myMethod<T>(T value)` → generic method
- `<T extends Base>` → tip kısıtlama (constraint)
- Dart koleksiyonları zaten generic olarak tasarlanmıştır
