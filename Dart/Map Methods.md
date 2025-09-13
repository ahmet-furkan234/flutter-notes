
Tamam TkMatE! Şimdi **Dart’ta Map ve Map Methods** konusunu detaylı şekilde inceleyelim. Map, **anahtar-değer (key-value) yapısı** ile veri saklamanın temel yoludur.

---

## 1. **Map Nedir?**

- Elemanlar **key-value (anahtar-değer)** çiftleri halinde saklanır.
- Her key benzersizdir, value herhangi bir tip olabilir.
- Sıra garanti edilmez (ancak Dart 2.0+ sürümlerinde ekleme sırası korunur).

```dart
Map<String, String> user = {
  "name": "TkMatE",
  "city": "Istanbul",
};

print(user); // {name: TkMatE, city: Istanbul}
```

- Boş Map: `Map<String, int> scores = {};` veya `Map<int, String> ids = Map();`

---

## 2. **Eleman Ekleme ve Güncelleme**

- Yeni key-value ekleme

```dart
user["age"] = "20";
print(user); // {name: TkMatE, city: Istanbul, age: 20}
```

- Var olan key’in değerini güncelleme

```dart
user["city"] = "Ankara";
print(user); // city güncellendi
```

- `putIfAbsent(key, () => value)` → Eğer key yoksa ekler

```dart
user.putIfAbsent("email", () => "tkmate@example.com");
```

---

## 3. **Eleman Silme**

- `remove(key)` → Key’e ait elemanı siler

```dart
user.remove("age");
print(user); // age silindi
```

- `clear()` → Tüm elemanları siler

```dart
user.clear();
print(user); // {}
```

---

## 4. **Eleman Erişimi ve Kontrol**

- Key ile değer okuma:

```dart
print(user["name"]); // TkMatE
```

- `containsKey(key)` → Key var mı?

```dart
print(user.containsKey("city")); // true
```

- `containsValue(value)` → Value var mı?

```dart
print(user.containsValue("Istanbul")); // true
```

- `isEmpty` / `isNotEmpty`

```dart
print(user.isNotEmpty); // true
```

- `length` → Eleman sayısı

```dart
print(user.length); // 2
```

---

## 5. **Map Üzerinde Döngü**

- `forEach((key, value) => …)`

```dart
user.forEach((key, value) {
  print("$key : $value");
});
```

- Key veya value listesi almak

```dart
var keys = user.keys.toList();      // [name, city]
var values = user.values.toList();  // [TkMatE, Istanbul]
```

---

## 6. **Map Dönüşümleri**

- `map((key, value) => MapEntry(newKey, newValue))` → Yeni Map oluşturur

```dart
var upperUser = user.map((key, value) => MapEntry(key.toUpperCase(), value.toUpperCase()));
print(upperUser); // {NAME: TKMATE, CITY: ISTANBUL}
```

- `entries` → Key-value iterable

```dart
for(var entry in user.entries){
  print("${entry.key} = ${entry.value}");
}
```

---

## 7. **Diğer Kullanışlı Metotlar**

- `update(key, (value) => newValue)` → Key’in değerini günceller

```dart
user.update("city", (value) => "Izmir");
```

- `update(key, (value) => newValue, ifAbsent: () => defaultValue)` → Key yoksa ekler
- `removeWhere((key, value) => condition)` → Şarta uyan elemanları siler

```dart
user.removeWhere((key, value) => key == "city");
```

- `putIfAbsent` → Key yoksa ekler

```dart
user.putIfAbsent("phone", () => "555-1234");
```

---

### ✅ Özet

- Map = Anahtar-değer yapısı
- Key benzersiz, value serbest
- Eleman ekleme, silme, güncelleme, arama ve döngü için birçok hazır metod mevcut
