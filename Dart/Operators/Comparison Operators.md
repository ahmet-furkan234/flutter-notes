
Bu operatörler, iki değeri karşılaştırmak için kullanılır ve her zaman **`bool` (true/false)** döner.

|Operatör|Açıklama|Örnek|
|---|---|---|
|`==`|Eşit mi?|`a == b`|
|`!=`|Eşit değil mi?|`a != b`|
|`<`|Küçük mü?|`a < b`|
|`>`|Büyük mü?|`a > b`|
|`<=`|Küçük veya eşit mi?|`a <= b`|
|`>=`|Büyük veya eşit mi?|`a >= b`|

---

## 1. Eşitlik (`==`)

```dart
void main() {
  int a = 10;
  int b = 10;
  int c = 5;

  print(a == b); // true
  print(a == c); // false
}
```

---

## 2. Eşit Değil (`!=`)

```dart
void main() {
  int a = 10;
  int b = 5;

  print(a != b); // true
  print(a != 10); // false
}
```

---

## 3. Küçük mü? (`<`)

```dart
void main() {
  int a = 3;
  int b = 5;

  print(a < b); // true
  print(b < a); // false
}
```

---

## 4. Büyük mü? (`>`)

```dart
void main() {
  int a = 7;
  int b = 2;

  print(a > b); // true
  print(b > a); // false
}
```

---

## 5. Küçük veya Eşit (`<=`)

```dart
void main() {
  int a = 5;

  print(a <= 5); // true
  print(a <= 10); // true
  print(a <= 3); // false
}
```

---

## 6. Büyük veya Eşit (`>=`)

```dart
void main() {
  int a = 8;

  print(a >= 8);  // true
  print(a >= 5);  // true
  print(a >= 10); // false
}
```

---

# 🎯 Özet

- `==` ve `!=` → eşitlik kontrolü
- `<`, `>`, `<=`, `>=` → sayısal büyüklük karşılaştırmaları
- Sonuçlar **true/false** döner
