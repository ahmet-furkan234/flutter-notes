
Fonksiyonlar, tekrar eden kodları **tek bir isim altında toplamak ve çağırmak** için kullanılır.

---

## 1. **Fonksiyon Tanımı (Basic Function)**

```dart
void sayHello() {
  print("Merhaba Dart!");
}

void main() {
  sayHello(); // Fonksiyon çağrısı
}
```

- `void` → fonksiyonun **geri dönüş değeri olmadığını** gösterir

---

## 2. **Parametreli Fonksiyonlar**

Fonksiyonlar veri alabilir ve bu verilerle işlem yapabilir.

```dart
void greet(String name) {
  print("Merhaba $name!");
}

void main() {
  greet("TkMatE"); // Merhaba TkMatE!
}
```

---

## 3. **Return (Değer Döndüren Fonksiyonlar)**

```dart
int add(int a, int b) {
  return a + b;
}

void main() {
  int result = add(5, 3);
  print(result); // 8
}
```

---

## 4. **Optional Parameters (Opsiyonel Parametreler)**

Dart’ta parametreler opsiyonel veya isimli olabilir.

### a) Positional Optional

```dart
void greet(String name, [String? title]) {
  if (title != null) {
    print("Merhaba $title $name");
  } else {
    print("Merhaba $name");
  }
}

void main() {
  greet("TkMatE");        // Merhaba TkMatE
  greet("TkMatE", "Mr."); // Merhaba Mr. TkMatE
}
```

### b) Named Optional

```dart
void greet({required String name, String? title}) {
  if (title != null) {
    print("Merhaba $title $name");
  } else {
    print("Merhaba $name");
  }
}

void main() {
  greet(name: "TkMatE");         // Merhaba TkMatE
  greet(name: "TkMatE", title: "Mr."); // Merhaba Mr. TkMatE
}
```

---

## 5. **Arrow Functions (Lambda / Tek Satırlık)**

Kısa fonksiyonlar için `=>` kullanılabilir.

```dart
int square(int x) => x * x;

void main() {
  print(square(5)); // 25
}
```

---

## 6. **Higher-order Functions (Fonksiyonları Parametre Olarak Kullanmak)**

Fonksiyon başka bir fonksiyona **parametre olarak** gönderilebilir.

```dart
void printResult(int Function(int, int) operation, int a, int b) {
  print(operation(a, b));
}

int add(int x, int y) => x + y;

void main() {
  printResult(add, 5, 3); // 8
}
```

---

# 🎯 Özet

- Fonksiyonlar tekrarlanan kodları yönetir
    
- `void` → dönüş yok
    
- Parametreler: zorunlu, opsiyonel, isimli
    
- `=>` → tek satırlık fonksiyon
    
- Fonksiyonlar parametre olarak gönderilebilir (higher-order functions)
    

---

TkMatE, sıradaki konu **Exception Handling (try, catch, finally, throw)**.  
Devam edelim mi?