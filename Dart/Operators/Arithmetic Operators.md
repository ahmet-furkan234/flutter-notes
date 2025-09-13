
Dart’ta sayılar (`int`, `double`, `num`) üzerinde kullanılan temel matematiksel operatörler şunlardır:

|Operatör|Açıklama|Örnek|
|---|---|---|
|`+`|Toplama|`a + b`|
|`-`|Çıkarma|`a - b`|
|`*`|Çarpma|`a * b`|
|`/`|Bölme (double sonuç)|`a / b`|
|`~/`|Tamsayı bölme (floor division)|`a ~/ b`|
|`%`|Mod (kalan)|`a % b`|
|`-`|Negatif işareti|`-a`|
|`++`|Artırma (ön/sonra)|`++a`, `a++`|
|`--`|Azaltma (ön/sonra)|`--a`, `a--`|

---

## 1. Toplama (`+`)

```dart
void main() {
  int a = 10;
  int b = 5;

  print(a + b); // 15
}
```

---

## 2. Çıkarma (`-`)

```dart
void main() {
  int a = 10;
  int b = 5;

  print(a - b); // 5
}
```

---

## 3. Çarpma (`*`)

```dart
void main() {
  int a = 10;
  int b = 5;

  print(a * b); // 50
}
```

---

## 4. Bölme (`/`)

👉 Her zaman **double** döner!

```dart
void main() {
  int a = 10;
  int b = 3;

  print(a / b); // 3.3333333333333335
}
```

---

## 5. Tamsayı Bölme (`~/`)

👉 Kesir kısmını atar, **tam sayı** döner.

```dart
void main() {
  int a = 10;
  int b = 3;

  print(a ~/ b); // 3
}
```

---

## 6. Mod (Kalan) (`%`)

```dart
void main() {
  int a = 10;
  int b = 3;

  print(a % b); // 1
}
```

---

## 7. Negatif İşareti (`-a`)

```dart
void main() {
  int a = 5;

  print(-a); // -5
}
```

---

## 8. Artırma ve Azaltma (`++` / `--`)

### Önce artır (`++a`)

```dart
void main() {
  int a = 5;

  print(++a); // 6 (önce artır, sonra yazdır)
  print(a);   // 6
}
```

### Sonra artır (`a++`)

```dart
void main() {
  int a = 5;

  print(a++); // 5 (önce yazdır, sonra artır)
  print(a);   // 6
}
```

### Önce azalt (`--a`)

```dart
void main() {
  int a = 5;

  print(--a); // 4
  print(a);   // 4
}
```

### Sonra azalt (`a--`)

```dart
void main() {
  int a = 5;

  print(a--); // 5
  print(a);   // 4
}
```

---

# 🎯 Özet

- `/` → her zaman **double** döner
    
- `~/` → **tam sayı** bölme
    
- `%` → kalan
    
- `++a` → önce artır, sonra kullan
    
- `a++` → önce kullan, sonra artır
    

---

👉 Bundan sonra sıradaki konu **Karşılaştırma Operatörleri (==, !=, <, >, <=, >=)**.  
Devam edelim mi?