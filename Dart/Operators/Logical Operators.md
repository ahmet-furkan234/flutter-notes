
Bu operatörler **boolean (true/false)** ifadeleri birleştirmek için kullanılır.

| Operatör | Açıklama                                        | Örnek    |
| -------- | ----------------------------------------------- | -------- |
| `&&`     | VE (and) → Her ikisi de **true** ise sonuç true | `a && b` |
| \| \|    | Veya                                            | `        |
| `!`      | DEĞİL (not) → Sonucun tersini alır              | `!a`     |

---

## 1. VE (&&)

👉 İki ifade de **true** olmalı.

```dart
void main() {
  bool a = true;
  bool b = false;

  print(a && b); // false
  print(a && true); // true
  print(b && false); // false
}
```

---

## 2. VEYA (||)

👉 En az biri **true** olmalı.

```dart
void main() {
  bool a = true;
  bool b = false;

  print(a || b); // true
  print(b || false); // false
  print(a || true); // true
}
```

---

## 3. DEĞİL (!)

👉 Boolean değerini tersine çevirir.

```dart
void main() {
  bool a = true;
  bool b = false;

  print(!a); // false
  print(!b); // true
}
```

---

## 4. Karma Örnek

Mantıksal operatörleri karşılaştırmalarla birlikte kullanalım:

```dart
void main() {
  int age = 20;
  bool hasId = true;

  // 18 yaş üstü ve kimliği var mı?
  print(age >= 18 && hasId); // true

  // 18 yaşından küçük veya kimlik var mı?
  print(age < 18 || hasId); // true
}
```

---

# 🎯 Özet

- `&&` → her iki koşul da doğru olmalı
- `||` → en az bir koşul doğru olmalı
- `!` → sonucu tersine çevirir
