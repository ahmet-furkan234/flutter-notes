
Atama operatörleri, bir değişkene **değer atamak** veya mevcut değerini güncellemek için kullanılır.

|Operatör|Açıklama|Örnek|
|---|---|---|
|`=`|Basit atama|`a = 5`|
|`+=`|Toplayarak atama|`a += 2` → `a = a + 2`|
|`-=`|Çıkararak atama|`a -= 2` → `a = a - 2`|
|`*=`|Çarparak atama|`a *= 2` → `a = a * 2`|
|`/=`|Böler atama (double sonuç)|`a /= 2` → `a = a / 2`|
|`~/=`|Tamsayı böler atama|`a ~/= 2` → `a = a ~/ 2`|
|`%=`|Mod alarak atama|`a %= 3` → `a = a % 3`|
|`??=`|Eğer değişken null ise değer ata|`a ??= 10`|

---

## 1. Basit Atama (`=`)

```dart
void main() {
  int a = 10;
  print(a); // 10
}
```

---

## 2. Toplayarak Atama (`+=`)

```dart
void main() {
  int a = 5;
  a += 3;  // a = a + 3
  print(a); // 8
}
```

---

## 3. Çıkararak Atama (`-=`)

```dart
void main() {
  int a = 10;
  a -= 4;  // a = a - 4
  print(a); // 6
}
```

---

## 4. Çarparak Atama (`*=`)

```dart
void main() {
  int a = 6;
  a *= 2;  // a = a * 2
  print(a); // 12
}
```

---

## 5. Bölerek Atama (`/=`)

👉 Her zaman **double** döner.

```dart
void main() {
  double a = 10;
  a /= 4;  // a = a / 4
  print(a); // 2.5
}
```

---

## 6. Tamsayı Bölme Ataması (`~/=`)

👉 Kesir kısmını atar.

```dart
void main() {
  int a = 10;
  a ~/= 3;  // a = a ~/ 3
  print(a); // 3
}
```

---

## 7. Mod Ataması (`%=`)

```dart
void main() {
  int a = 10;
  a %= 4;  // a = a % 4
  print(a); // 2
}
```

---

## 8. Null-aware Atama (`??=`)

👉 Eğer değişken **null ise** değer atanır.

```dart
void main() {
  int? a;
  a ??= 10;   // a null olduğu için 10 atanır
  print(a);   // 10

  a ??= 20;   // a artık null değil, bu yüzden değişmez
  print(a);   // 10
}
```

---

# 🎯 Özet

- `=` → normal atama
    
- `+=`, `-=`, `*=`, `/=`, `~/=`, `%=` → kısayollar
    
- `??=` → sadece null ise değer ata
    

---

👉 Bundan sonra sırada **Bitwise (bit düzeyinde) Operatörler (&, |, ^, ~, <<, >>)** var.  
Onlara da geçelim mi?