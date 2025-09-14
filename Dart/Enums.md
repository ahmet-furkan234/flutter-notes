
# 🟦 Enums (Sabitler Kümesi)

**Enum**, sabit ve sınırlı değerleri temsil etmek için kullanılan özel bir türdür.

- Kodun okunabilirliğini artırır.
- Yanlış değer atama riskini azaltır.
- Dart’ta `enum` anahtar kelimesi ile tanımlanır.

---

## 🔹 1. Basit Enum Örneği

```dart
enum Day { Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday }

void main() {
  Day today = Day.Monday;

  print(today);        // Day.Monday
  print(today.name);   // Monday
  print(today.index);  // 0
}
```

📌 Açıklamalar:

- `name` → enum değerinin adı (string).
- `index` → enum değerinin sırası (0’dan başlar).

---

## 🔹 2. Switch-case ile Kullanım

```dart
enum Color { Red, Green, Blue }

void main() {
  Color favorite = Color.Green;

  switch(favorite) {
    case Color.Red:
      print("Kırmızı");
      break;
    case Color.Green:
      print("Yeşil");
      break;
    case Color.Blue:
      print("Mavi");
      break;
  }
}
```

📌 Enum’ları **switch-case** ile kontrol etmek çok yaygındır.

---

## 🔹 3. Enum’a Ek Özellikler Eklemek (Dart 2.17+)

Dart artık enum’lara **field, getter ve constructor** eklemeyi destekliyor.

```dart
enum VehicleType {
  Car(4),
  Bike(2),
  Truck(6);

  final int wheels;
  const VehicleType(this.wheels);
}

void main() {
  print(VehicleType.Car.wheels);   // 4
  print(VehicleType.Bike.wheels);  // 2
}
```

📌 Artık enum **sadece sabit değer değil**, aynı zamanda **veri taşıyabiliyor**.

---

## 🔹 4. Enum ile Method Kullanımı

```dart
enum Mood {
  Happy,
  Sad,
  Angry;

  void describe() {
    switch(this) {
      case Mood.Happy:
        print("Mutluyum 😊");
        break;
      case Mood.Sad:
        print("Üzgünüm 😢");
        break;
      case Mood.Angry:
        print("Kızgınım 😡");
        break;
    }
  }
}

void main() {
  Mood todayMood = Mood.Happy;
  todayMood.describe(); // Mutluyum 😊
}
```

📌 Enum artık **method da barındırabilir**, sınıf gibi davranır.

---

## 🔹 5. Özet

- Enum → sınırlı sabit değerler için kullanılır.
- `name` → enum adını verir.
- `index` → enum sırasını verir.
- Dart 2.17+ → enum field, constructor ve method içerebilir.
- Switch-case veya doğrudan kullanım ile kontrollü şekilde değer seçilebilir.

---

TkMatE, bir sonraki konu **Generics (Generic Class & Method)**.  
Bunu detaylı olarak ele alalım mı?