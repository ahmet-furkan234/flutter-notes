
Aynen doğru yakalamışsın TkMatE ✅

- **Positional Parameters (Sıralı)** → Parametreler **verildiği sıraya göre** eşleşir.
- **Named Parameters (İsme Göre)** → Parametreler **isim verilerek** eşleşir, sıranın önemi yoktur.

---

# 🔹 1. Positional Parameters

```dart
void greet(String firstName, String lastName) {
  print("Merhaba $firstName $lastName");
}

void main() {
  greet("Ahmet", "Furkan"); // Sıra önemli!
  // greet("Furkan", "Ahmet"); // Yanlış sıralama → farklı çıktı
}
```

📌 Burada parametreler **sırasına göre** eşleşti.

---

# 🔹 2. Named Parameters

```dart
void greet({String? firstName, String? lastName}) {
  print("Merhaba $firstName $lastName");
}

void main() {
  greet(firstName: "Ahmet", lastName: "Furkan"); // İsimle veriyoruz
  greet(lastName: "Furkan", firstName: "Ahmet"); // Sıra önemli değil
}
```

📌 Burada parametreler **isimlerine göre** eşleşti.

---

# 🔹 3. Default Değer ile Named Parameters

```dart
void greet({String firstName = "Misafir", String lastName = ""}) {
  print("Merhaba $firstName $lastName");
}

void main() {
  greet(); // Merhaba Misafir
  greet(firstName: "TkMatE"); // Merhaba TkMatE
}
```

---

# ✅ Özet

- **Positional** → `greet("Ahmet", "Furkan")` → sıraya göre
- **Named** → `greet(firstName: "Ahmet", lastName: "Furkan")` → isme göre

---

İstersen TkMatE, sırada **inheritance (kalıtım)** konusuna geçelim mi, yoksa önce Dart’taki **optional parameters (hem positional hem named)** farklarını daha derin inceleyelim mi?