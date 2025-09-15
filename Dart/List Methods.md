a
## 1. **List Oluşturma**

```dart
List<int> numbers = [1, 2, 3, 4, 5];
List<String> fruits = ["Elma", "Muz", "Armut"];
```

- Boş liste: `List<int> empty = [];`
- Sabit uzunluk: `List.filled(5, 0)` → 5 elemanlı, 0 ile dolu.

---

## 2. **Eleman Ekleme**

- `add(element)` → Liste sonuna ekler

```dart
numbers.add(6);
print(numbers); // [1, 2, 3, 4, 5, 6]
```

- `addAll(list)` → Birden fazla eleman ekler

```dart
numbers.addAll([7, 8]);
print(numbers); // [1, 2, 3, 4, 5, 6, 7, 8]
```

- `insert(index, element)` → Belirli konuma ekler

```dart
numbers.insert(0, 0);
print(numbers); // [0, 1, 2, 3, 4, 5, 6, 7, 8]
```

- `insertAll(index, list)` → Belirli konuma birden fazla eleman ekler

```dart
numbers.insertAll(3, [99, 100]);
print(numbers); // [0, 1, 2, 99, 100, 3, 4, 5, 6, 7, 8]
```

---

## 3. **Eleman Silme**

- `remove(element)` → İlk bulduğu elemanı siler

```dart
numbers.remove(100);
print(numbers); // 100 silindi
```

- `removeAt(index)` → Belirli indeksteki elemanı siler

```dart
numbers.removeAt(0);
print(numbers); // İlk eleman silindi
```

- `removeLast()` → Son elemanı siler

```dart
numbers.removeLast();
```

- `removeWhere(condition)` → Şarta uyan elemanları siler

```dart
numbers.removeWhere((x) => x > 5);
```

- `clear()` → Tüm elemanları siler

```dart
numbers.clear();
```

---

## 4. **Eleman Erişimi ve Bilgi Alma**

- `numbers[index]` → Belirli indeks
- `first` → İlk eleman
- `last` → Son eleman
- `length` → Eleman sayısı
- `isEmpty` / `isNotEmpty` → Boş mu kontrolü

```dart
print(numbers.first); // 0
print(numbers.last);  // Son eleman
print(numbers.length); // 10
print(numbers.isNotEmpty); // true
```

---

## 5. **Arama ve Filtreleme**

- `contains(element)` → Eleman var mı?

```dart
print(numbers.contains(3)); // true
```

- `indexOf(element)` → Elemanın indeksi

```dart
print(numbers.indexOf(3)); // 2
```

- `lastIndexOf(element)` → Son indeks
- `where((x) => condition)` → Filtreleme, iterable döner

```dart
var even = numbers.where((x) => x % 2 == 0);
print(even.toList()); // Çift sayılar
```

---

## 6. **Listeyi Dönüştürme / İşleme**

- `map((x) => x*2)` → Her elemanı değiştirir, iterable döner

```dart
var doubleNumbers = numbers.map((x) => x*2).toList();
```

- `forEach((x) => print(x))` → Elemanları tek tek işler

```dart
numbers.forEach((x) => print(x));
```

- `sort()` → Sıralama

```dart
numbers.sort(); // Artan
numbers.sort((a, b) => b.compareTo(a)); // Azalan
```

- `reversed` → Ters sırada iterable döner

```dart
print(numbers.reversed.toList());
```

---

## 7. **Alt Liste / Kopya Liste**

- `sublist(start, [end])` → Belirli aralığı alır

```dart
var sub = numbers.sublist(2, 5);
```

- `toList()` → Iterable → List

```dart
var newList = numbers.where((x) => x>2).toList();
```

- `join(separator)` → Elemanları string olarak birleştirir

```dart
print(fruits.join(", ")); // Elma, Muz, Armut
```

---

## 8. **Listeyi Dönüştürme ve Kopyalama**

```dart
var copy = List.from(numbers); // Listeyi kopyalar
var filled = List.filled(5, 0); // Sabit uzunluk
```
