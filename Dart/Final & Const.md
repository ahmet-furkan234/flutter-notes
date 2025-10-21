o
## 1. **`final`**

- **Bir kez atanabilir**, sonradan değiştirilemez.
- Değer **çalışma zamanında** (runtime) atanabilir.
- Tipik olarak **değeri değişmeyecek ama runtime’da belli olan** veriler için kullanılır.

```dart
void main() {
  final name = "TkMatE";   // String sabit
  print(name);

  // name = "Ahmet"; // HATA! final değiştirilemez

  final DateTime now = DateTime.now(); // runtime’da değer atanabilir
  print(now);
}
```

- Avantaj:
    - Değişmeyecek değerleri güvenle saklayabilirsin
- Dezavantaj:
    - Compile-time sabiti değildir, her runtime’da yeniden atanabilir

---

## 2. **`const`**

- **Derleme zamanında (compile-time) sabittir**, program boyunca değişmez.
- `const` ile tanımlanan değerler **mutlak sabittir**.

```dart
void main() {
  const pi = 3.14;
  print(pi);

  // pi = 3.1415; // HATA! const değiştirilemez

  const List<int> numbers = [1, 2, 3]; // const list
  // numbers.add(4); // HATA! const list değiştirilemez
}
```

- Özellikler:
    - Compile-time sabiti: Program çalışmadan önce değeri belli olmalı
    - Immutable (değiştirilemez)

---

## 3. **final vs const Karşılaştırması**

|Özellik|`final`|`const`|
|---|---|---|
|Değer atanma zamanı|Runtime|Compile-time|
|Değiştirilebilir mi|Hayır|Hayır|
|Koleksiyonlarda|Değiştirilebilir elemanlar var|Tamamen immutable|
|Örnek|`final now = DateTime.now();`|`const pi = 3.14;`|

---

## 4. **Örnekler**

```dart
void main() {
  final city = "Istanbul";
  const country = "Turkey";

  final DateTime today = DateTime.now();
  const double pi = 3.1415;

  print("City: $city");
  print("Country: $country");
  print("Today: $today");
  print("Pi: $pi");

  // const list
  const List<String> fruits = ["Elma", "Muz"];
  // fruits.add("Armut"); // HATA!

  // final list
  final List<String> colors = ["Kırmızı", "Mavi"];
  colors.add("Yeşil"); // TAMAM, final list değiştirilebilir ama list objesi değiştirilemez
  print(colors); // [Kırmızı, Mavi, Yeşil]
}
```

- **Önemli Not:**
    - `final list` → liste objesi değişmez ama içindeki elemanlar değiştirilebilir.
    - `const list` → hem obje hem içi tamamen değişmez.
