
Dart’ta fonksiyon/metot parametreleri üç şekilde tanımlanabilir:

1. **Positional Required** → Sıralı, zorunlu
2. **Positional Optional `[ ]`** → Sıralı, opsiyonel
3. **Named Optional `{ }`** → İsimle, opsiyonel veya required

---

## 1️⃣ Positional Required Parameters

- **Normal parantez `( )`** içinde tanımlanır.
- **Zorunludur** → fonksiyon/metot çağrılırken mutlaka verilmelidir.
- **Sıra önemlidir**.

```dart
void greet(String firstName, String lastName) {
  print("Merhaba $firstName $lastName");
}

void main() {
  greet("Ahmet", "Furkan"); // ✅ doğru
  // greet("Furkan"); // ❌ hata → eksik parametre
}
```

---

## 2️⃣ Positional Optional Parameters `[ ]`

- Köşeli parantez `[ ]` ile tanımlanır.
- **Opsiyoneldir** → verilmezse `null` olur veya default değer atanabilir.
- **Sıra önemli** → hangi sıradaysa ona göre eşleşir.
- **`required` kullanılamaz**.

```dart
void greet(String name, [String? title = ""]) {
  print("Merhaba $title $name");
}

void main() {
  greet("Ahmet");          // Merhaba  Ahmet
  greet("Ahmet", "Bey");   // Merhaba Bey Ahmet
}
```

- `[String? title = ""]` → opsiyonel positional parametre, default değeri var
    

---

## 3️⃣ Named Optional Parameters `{ }`

- Süslü parantez `{ }` ile tanımlanır.
- **İsimle çağrılır**, sıra önemli değildir.
- **Opsiyonel veya required** olabilir.
- Default değer atanabilir.

```dart
void greet({required String name, String title = ""}) {
  print("Merhaba $title $name");
}

void main() {
  // greet(); ❌ hata → name required
  greet(name: "Ahmet");       // Merhaba  Ahmet
  greet(title: "Bey", name: "Ahmet"); // Merhaba Bey Ahmet
}
```

---

## 4️⃣ Positional + Named Kombinasyonu

- Dart’ta **zorunlu positional parametreler** + **named parametreler** birlikte kullanılabilir.

```dart
void greet(String firstName, String lastName, {String title = ""}) {
  print("Merhaba $title $firstName $lastName");
}

void main() {
  greet("Ahmet", "Furkan");                // Merhaba  Ahmet Furkan
  greet("Ahmet", "Furkan", title: "Bey"); // Merhaba Bey Ahmet Furkan
}
```

- Sıralı parametreler `( )` → zorunlu
- Süslü parantez `{ }` → opsiyonel, isimle

---

## 5️⃣ Default Values & Null Safety

- Opsiyonel parametrelerde default değer kullanmak tavsiye edilir.
- Null safety ile parametreleri nullable (`String?`) veya required yapabilirsin.

```dart
void greet([String name = "Misafir"]) {
  print("Merhaba $name");
}

void main() {
  greet();            // Merhaba Misafir
  greet("TkMatE");    // Merhaba TkMatE
}
```

- Named parametrelerde de default değer kullanılabilir:

```dart
void greet({String name = "Misafir"}) {
  print("Merhaba $name");
}
```

---

## 6️⃣ Özet Tablo

|Tür|Sembol|Zorunlu|Sıra Önemli|Default / required|
|---|---|---|---|---|
|Positional Required|`( )`|Evet|Evet|-|
|Positional Optional|`[ ]`|Hayır|Evet|Default değer verilebilir, required **olamaz**|
|Named Optional|`{ }`|Hayır / `required` ile zorunlu yapılabilir|Hayır|Default değer verilebilir|

---

💡 **Kafa karıştıran noktalar**:

1. `[ ]` → Sadece opsiyonel positional, required kullanılamaz.
2. `{ }` → Opsiyonel veya required olabilir, **isimle çağrılır**, sıra önemli değil.
3. Positional + Named aynı fonksiyonda birlikte kullanılabilir, fakat **positional önce**, **named sonra** gelir.
