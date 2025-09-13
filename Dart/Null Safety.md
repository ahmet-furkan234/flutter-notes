
Dart, **null değer hatalarını (NullReferenceException)** engellemek için **null safety** sistemini getiriyor.  
Yani bir değişkenin **null olabilir mi / olamaz mı** bilgisini **derleme (compile-time)** aşamasında kontrol ediyor.

---

## 1. Normal (Non-nullable) Değişkenler

Varsayılan olarak Dart’ta değişkenler **null olamaz**.

```dart
void main() {
  int a = 5; 
  // int b;   // HATA! Başlatmadan kullanamazsın.
  
  print(a); // 5
}
```

👉 `int` yazarsan bu değişken **asla null olamaz**.

---

## 2. Nullable Değişkenler (`?`)

Bir değişkenin **null olabileceğini** belirtmek için **`?`** kullanılır.

```dart
void main() {
  int? age = null;   // null olabilir
  print(age);        // null yazdırır
  
  age = 25;
  print(age);        // 25
}
```

👉 `int?` → “int olabilir ya da null olabilir”

---

## 3. Null Assertion Operator (`!`)

Eğer bir değişkenin **null olmayacağından emin isen**, `!` kullanabilirsin.  
Ama yanılırsan **runtime hatası** alırsın ⚠️

```dart
void main() {
  int? number = 10;
  print(number!);  // 10

  int? value = null;
  print(value!);   // HATA! Null check failed
}
```

---

## 4. Null-aware Operatorler

Dart, null ile güvenli çalışmak için özel operatörler sunuyor.

### a) `??` → Varsayılan değer

```dart
void main() {
  String? name;
  print(name ?? "Bilinmiyor"); // Bilinmiyor
}
```

### b) `??=` → Eğer null ise değer ata

```dart
void main() {
  int? x;
  x ??= 10;   // x null olduğu için 10 atanır
  print(x);   // 10
}
```

### c) `?.` → Null ise işlemi yapma

```dart
void main() {
  String? text;
  print(text?.length); // null (hata değil!)
  
  text = "Dart";
  print(text?.length); // 4
}
```

---

## 5. `late` Anahtar Kelimesi

Bir değişkeni **hemen değil, sonra başlatacağını** belirtir.  
Ama **null olmadan garanti** eder.

```dart
void main() {
  late String message;

  message = "Merhaba Dart!";
  print(message); // Merhaba Dart!
}
```

⚠️ Eğer `late` ile tanımlayıp hiç değer vermezsen → **runtime hatası**.

---

## 6. `required` Parametre

Fonksiyonlarda parametrenin **null olmamasını zorunlu kılar**.  
Genelde **isimli parametreler** ile birlikte kullanılır.

```dart
void greet({required String name}) {
  print("Merhaba $name!");
}

void main() {
  greet(name: "TkMatE"); // ✅ Çalışır
  // greet();            // ❌ Hata! name zorunlu
}
```

---

# ✅ Özet

- `int x` → null olamaz
- `int? x` → null olabilir
- `x!` → “eminim null değil” (ama riskli)
- `??`, `??=`, `?.` → null-aware operatörler
- `late` → sonra başlatılacak, ama null olmayacak
- `required` → fonksiyon parametresi boş geçilemez