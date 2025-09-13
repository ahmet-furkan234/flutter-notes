
Dart, **Google** tarafından geliştirilen, özellikle **Flutter uygulamaları** için kullanılan modern, güçlü ve tip güvenli bir programlama dilidir.

- **Statically typed**: Değişken tiplerini derleme sırasında kontrol eder.
- **Object-oriented**: Sınıf ve nesne tabanlıdır.
- **Asenkron programlama desteği**: `Future` ve `async/await` ile güçlü async işlemler yapılabilir.

---

## 2. Değişkenler ve Veri Tipleri

Dart’ta değişkenler iki şekilde tanımlanabilir:

### a) Tip Belirterek

```dart
int age = 25;
double height = 1.75;
String name = "TkMatE";
bool isStudent = true;
```

### b) `var` ile (tip otomatik belirlenir)

```dart
var city = "Istanbul"; // String olarak algılar
var score = 95;        // int olarak algılar
```

### c) `dynamic` ile (tip değişebilir)

```dart
dynamic value = 10;
value = "Hello"; // Hata vermez, tipi değişir
```

**Not:** Mümkünse `var` veya tip belirterek kullanmak daha güvenlidir.

---

## 3. Sabitler ve Final

- `const`: Derleme zamanında sabit.
- `final`: Çalışma zamanında bir kez atanabilir.

```dart
const pi = 3.14;       // Değiştirilemez
final name = "TkMatE"; // Bir kez atanabilir
```

---

## 4. Operatörler

- **Aritmetik**: `+ - * / ~/ %`
- **Atama**: `= += -= *= /=`
- **Karşılaştırma**: `== != > < >= <=`
- **Mantıksal**: `&& || !`

```dart
int a = 10;
int b = 3;
print(a + b); // 13
print(a ~/ b); // 3 (tam sayı bölme)
```

---

## 5. Kontrol Yapıları

### a) If-else

```dart
int score = 85;
if(score >= 90) {
  print("A aldın");
} else if(score >= 75) {
  print("B aldın");
} else {
  print("C aldın");
}
```

### b) Switch-case

```dart
String grade = "B";
switch(grade) {
  case "A": print("Mükemmel"); break;
  case "B": print("İyi"); break;
  default: print("Çalışmaya devam");
}
```

---

## 6. Döngüler

### a) For

```dart
for(int i = 0; i < 5; i++){
  print(i);
}
```

### b) While

```dart
int i = 0;
while(i < 5){
  print(i);
  i++;
}
```

### c) For-in (liste üzerinde gezinme)

```dart
List<String> fruits = ["Elma", "Armut", "Muz"];
for(var fruit in fruits){
  print(fruit);
}
```

---

## 7. Fonksiyonlar

```dart
// Parametresiz
void greet(){
  print("Merhaba TkMatE!");
}

// Parametreli
int sum(int a, int b){
  return a + b;
}

// Lambda (tek satır)
int multiply(int a, int b) => a * b;

void main(){
  greet();
  print(sum(5, 3));       // 8
  print(multiply(4, 2));  // 8
}
```

---

## 8. Listeler ve Map’ler

### Listeler

```dart
List<int> numbers = [1, 2, 3, 4];
numbers.add(5);
print(numbers[2]); // 3
```

### Map (Sözlük)

```dart
Map<String, String> user = {
  "name": "TkMatE",
  "city": "Istanbul"
};
print(user["name"]); // TkMatE
```

---

## 9. Null Safety

Dart 2.12+ ile **null güvenliği** geldi.

- Tip sonuna `?` eklenirse null olabilir.
- Yoksa null ataması hata verir.

```dart
String? middleName; // null olabilir
String lastName = "Arpacı"; // null olamaz
```

---

## 10. Sınıflar (Classes)

```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  void introduce() {
    print("Ben $name, $age yaşındayım");
  }
}

void main(){
  var person = Person("TkMatE", 20);
  person.introduce();
}
```
