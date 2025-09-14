
Kontrol yapıları, kodun **hangi sırayla ve hangi koşullarda çalışacağını** belirler.

---

## 1. **if / else**

### a) if

Belirli bir koşul **true** ise çalışır.

```dart
void main() {
  int age = 20;

  if (age >= 18) {
    print("Reşitsiniz");
  }
}
```

---

### b) if-else

Koşul false ise **else bloğu** çalışır.

```dart
void main() {
  int age = 16;

  if (age >= 18) {
    print("Reşitsiniz");
  } else {
    print("Reşit değilsiniz");
  }
}
```

---

### c) if-else if-else

Birden fazla koşul kontrolü için kullanılır.

```dart
void main() {
  int score = 75;

  if (score >= 90) {
    print("A aldınız");
  } else if (score >= 75) {
    print("B aldınız");
  } else if (score >= 60) {
    print("C aldınız");
  } else {
    print("F aldınız");
  }
}
```

---

## 2. **switch / case**

- Bir değişkenin **birden fazla değerini** kontrol etmek için kullanılır.

```dart
void main() {
  String day = "Pazartesi";

  switch (day) {
    case "Pazartesi":
      print("Haftanın ilk günü");
      break;
    case "Cuma":
      print("Hafta sonuna yaklaşıyoruz");
      break;
    default:
      print("Orta gün");
  }
}
```

- **break** → case’den çıkmak için gerekli
- **default** → hiçbir case eşleşmezse çalışır

---

## 3. **Loops (Döngüler)**

### a) for

Belirli sayıda tekrar için kullanılır.

```dart
void main() {
  for (int i = 0; i < 5; i++) {
    print("Döngü: $i");
  }
}
```

---

### b) while

Koşul doğru olduğu sürece tekrar eder.

```dart
void main() {
  int i = 0;
  while (i < 5) {
    print("While döngüsü: $i");
    i++;
  }
}
```

---

### c) do-while

Koşul **sonra** kontrol edilir → en az bir kez çalışır.

```dart
void main() {
  int i = 0;
  do {
    print("Do-while döngüsü: $i");
    i++;
  } while (i < 5);
}
```

---

### d) for-in

Koleksiyonlar üzerinde iterasyon için kullanılır.

```dart
void main() {
  List<String> fruits = ["Elma", "Muz", "Çilek"];

  for (var fruit in fruits) {
    print(fruit);
  }
}
```

---

### e) forEach (Collection method)

Koleksiyon üzerinde fonksiyon ile iterasyon yapar.

```dart
void main() {
  List<int> numbers = [1, 2, 3];

  numbers.forEach((number) {
    print(number * 2);
  });
}
```

---

## 4. **Break & Continue**

- **break** → Döngüyü tamamen sonlandırır
- **continue** → Döngünün bir sonraki iterasyonuna geçer

```dart
void main() {
  for (int i = 0; i < 5; i++) {
    if (i == 3) break;
    print(i); // 0,1,2
  }

  for (int i = 0; i < 5; i++) {
    if (i == 2) continue;
    print(i); // 0,1,3,4
  }
}
```

---

# 🎯 Özet

- `if / else` → koşul bazlı karar
- `switch / case` → birden fazla değer kontrolü
- Döngüler → tekrarlar: `for`, `while`, `do-while`, `for-in`, `forEach`
- `break / continue` → döngü kontrolü
