
Bitwise operatörler, sayıları **ikili (binary)** düzeyde işler. Yani `0` ve `1` bitlerini doğrudan manipüle eder.

|Operatör|Açıklama|Örnek|
|---|---|---|
|`&`|Bitwise AND (VE)|`a & b`|
|`|`|Bitwise OR (VEYA)|
|`^`|Bitwise XOR (özel veya)|`a ^ b`|
|`~`|Bitwise NOT (değil)|`~a`|
|`<<`|Bitwise sola kaydırma|`a << n`|
|`>>`|Bitwise sağa kaydırma|`a >> n`|

---

## 1. Bitwise AND (`&`)

👉 Her iki bit de `1` ise sonuç `1`.

```dart
void main() {
  int a = 6; // 110 (binary)
  int b = 3; // 011

  print(a & b); // 2 (010)
}
```

---

## 2. Bitwise OR (`|`)

👉 En az biri `1` ise sonuç `1`.

```dart
void main() {
  int a = 6; // 110
  int b = 3; // 011

  print(a | b); // 7 (111)
}
```

---

## 3. Bitwise XOR (`^`)

👉 Bitler farklı ise `1`, aynı ise `0`.

```dart
void main() {
  int a = 6; // 110
  int b = 3; // 011

  print(a ^ b); // 5 (101)
}
```

---

## 4. Bitwise NOT (`~`)

👉 Tüm bitleri ters çevirir. (İşaretli sayılar için **two’s complement** mantığı kullanılır.)

```dart
void main() {
  int a = 6; // 0000...0110
  print(~a); // -7
}
```

> Burada olay şu: `~a = -(a+1)`. Yani `~6 = -7`.

---

## 5. Sola Kaydırma (`<<`)

👉 Bitleri sola kaydırır. Her kaydırma 2 ile çarpma anlamına gelir.

```dart
void main() {
  int a = 3; // 011

  print(a << 1); // 6  (110)
  print(a << 2); // 12 (1100)
}
```

---

## 6. Sağa Kaydırma (`>>`)

👉 Bitleri sağa kaydırır. Her kaydırma 2’ye bölme (tamsayı) anlamına gelir.

```dart
void main() {
  int a = 12; // 1100

  print(a >> 1); // 6  (0110)
  print(a >> 2); // 3  (0011)
}
```

---

# 🎯 Özet

- `&` → AND → ikisi de 1 olmalı
    
- `|` → OR → en az biri 1 olmalı
    
- `^` → XOR → farklıysa 1
    
- `~` → NOT → bitleri ters çevir
    
- `<<` → sola kaydır (2 ile çarpma)
    
- `>>` → sağa kaydır (2’ye bölme)
    

---

👉 Bundan sonra sırada **Type Test Operatörleri (`is`, `is!`, `as`)** var.  
Onlara geçelim mi?