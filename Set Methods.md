
- Aynı elemandan sadece **bir tane** bulundurur.
- Eleman sırası garanti edilmez.
- Koleksiyonlarda **tekrar eden verileri önlemek** için idealdir.

```dart
Set<int> numbers = {1, 2, 3, 3, 4};
print(numbers); // {1, 2, 3, 4}  (3 tekrar etmedi)
```

- Boş Set: `Set<int> empty = {};` veya `Set<int> empty = Set();`

---

## 2. **Eleman Ekleme**

- `add(element)` → Tek eleman ekler

```dart
numbers.add(5);
print(numbers); // {1, 2, 3, 4, 5}
```

- `addAll(iterable)` → Birden fazla eleman ekler

```dart
numbers.addAll([6, 7, 3]);
print(numbers); // {1, 2, 3, 4, 5, 6, 7} (3 zaten vardı)
```

---

## 3. **Eleman Silme**

- `remove(element)` → Belirli elemanı siler

```dart
numbers.remove(4);
print(numbers); // {1, 2, 3, 5, 6, 7}
```

- `removeWhere(condition)` → Şarta uyan elemanları siler

```dart
numbers.removeWhere((x) => x > 5);
print(numbers); // {1, 2, 3, 5}
```

- `clear()` → Tüm elemanları siler

```dart
numbers.clear();
print(numbers); // {}
```

---

## 4. **Eleman Arama ve Bilgi Alma**

- `contains(element)` → Eleman var mı?

```dart
print(numbers.contains(3)); // true
```

- `isEmpty` / `isNotEmpty` → Boş mu kontrol

```dart
print(numbers.isNotEmpty); // true
```

- `length` → Eleman sayısı

```dart
print(numbers.length); // 5
```

---

## 5. **Set Üzerinde Dönüşüm**

- `forEach((x) => print(x))` → Elemanları tek tek işler

```dart
numbers.forEach((x) => print(x));
```

- `map((x) => x*2)` → Her elemanı değiştirir (Iterable döner)

```dart
var doubleNumbers = numbers.map((x) => x*2);
print(doubleNumbers.toList()); // [2, 4, 6, 10, 0 gibi]
```

- `where((x) => condition)` → Filtreleme, iterable döner

```dart
var even = numbers.where((x) => x % 2 == 0);
print(even.toList()); // Çift sayılar
```

- `union(otherSet)` → İki seti birleştirir

```dart
var setA = {1, 2, 3};
var setB = {3, 4, 5};
print(setA.union(setB)); // {1, 2, 3, 4, 5}
```

- `intersection(otherSet)` → Ortak elemanlar

```dart
print(setA.intersection(setB)); // {3}
```

- `difference(otherSet)` → Fark elemanlar

```dart
print(setA.difference(setB)); // {1, 2}
```

---

## 6. **Diğer Kullanışlı Metotlar**

- `toList()` → Set’i Listeye dönüştürür

```dart
List<int> numberList = numbers.toList();
```

- `first` / `last` → İlk ve son eleman (sıra garantisi yok)

```dart
print(numbers.first);
print(numbers.last);
```

- `containsAll(iterable)` → Tüm elemanlar var mı?

```dart
print(numbers.containsAll([1, 3])); // true
```

---

### ✅ Özet

- Set = Tekrarsız veri, sırasız.
- Eleman ekleme, silme ve arama metodları List’e benzer ama **tekrarlara izin vermez**.
- Kümelerle yapılan işlemler (`union`, `intersection`, `difference`) List’te yoktur.
