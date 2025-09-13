Tamam TkMatE 🚀 Şimdi **Exception Handling (Hata Yönetimi)** konusuna geçelim.

---

# ⚠️ Dart Exception Handling (Hata Yönetimi)

Program çalışırken beklenmeyen durumlar oluşabilir (ör: sıfıra bölme, dosya bulunamama, yanlış tip).  
Dart, bu hataları **try-catch-finally** blokları ile yönetmemizi sağlar.

---

## 1. **try-catch**

- `try` bloğu içinde hata olabilecek kod yazılır.
- Hata oluşursa `catch` bloğu çalışır.

```dart
void main() {
  try {
    int result = 10 ~/ 0; // Hata! Sıfıra bölme
    print(result);
  } catch (e) {
    print("Hata oluştu: $e");
  }
}
```

- `e` → hatanın açıklamasını tutar (`Exception` veya `Error` nesnesi)

---

## 2. **catch ile stack trace**

```dart
void main() {
  try {
    int result = 10 ~/ 0;
  } catch (e, s) {
    print("Hata: $e");
    print("Stack Trace:\n$s");
  }
}
```

- `s` → hatanın oluştuğu yeri gösterir, debugging için kullanışlıdır

---

## 3. **on**

- Belirli bir hata türünü yakalamak için kullanılır.

```dart
void main() {
  try {
    int result = 10 ~/ 0;
  } on IntegerDivisionByZeroException {
    print("Sıfıra bölme hatası!");
  }
}
```

---

## 4. **finally**

- Hata olsun veya olmasın **her zaman çalışan blok**

```dart
void main() {
  try {
    int result = 10 ~/ 2;
    print(result);
  } catch (e) {
    print("Hata: $e");
  } finally {
    print("Bu blok her zaman çalışır");
  }
}
```

---

## 5. **throw**

- Kendi hatamızı fırlatabiliriz.

```dart
void checkAge(int age) {
  if (age < 18) {
    throw Exception("18 yaşından küçük olamazsınız!");
  }
}

void main() {
  try {
    checkAge(15);
  } catch (e) {
    print("Hata: $e");
  }
}
```

---

# 🎯 Özet

- `try` → hata olabilecek kod
- `catch` → hatayı yakalar
- `on` → belirli tip hatayı yakalar
- `finally` → her zaman çalışır
- `throw`→ kendi hatamızı fırlatır
