
## 1. **int (Tam Sayılar)**

- Tamsayıları tutar (negatif, pozitif ve 0).
- Ondalık sayı içermez.

```dart
int age = 25;
int year = 2025;

print(age);  // 25
print(year); // 2025
```

**İşlemler:**

```dart
int a = 10;
int b = 3;

print(a + b); // 13
print(a - b); // 7
print(a * b); // 30
print(a ~/ b); // 3 (tam sayı bölme)
print(a % b); // 1 (mod)
```

---

## 2. **double (Ondalık Sayılar)**

- Kesirli sayıları tutar.
- Ondalık hassasiyet gerektiren değerler için kullanılır.

```dart
double height = 1.75;
double price = 99.99;

print(height); // 1.75
print(price);  // 99.99
```

**İşlemler:**

```dart
double a = 5.5;
double b = 2.0;

print(a + b); // 7.5
print(a / b); // 2.75
```

---

## 3. **String (Metinler)**

- Karakter dizilerini tutar.
- Çift `"` veya tek `'` ile tanımlanabilir.

```dart
String name = "TkMatE";
String city = 'Istanbul';

print("Merhaba $name, $city'de yaşıyor."); // String interpolation
```

**Önemli Özellikler:**

- `+` ile birleştirme:

```dart
String first = "Ahmet";
String last = "Furkan";
print(first + " " + last); // Ahmet Furkan
```

- `length`, `toUpperCase()`, `toLowerCase()` gibi metodlar:

```dart
print(name.length);       // 6
print(name.toUpperCase()); // TKMAT
```

---

## 4. **bool (Mantıksal Değerler)**

- Sadece `true` veya `false` değerlerini alır.
- Koşul ifadelerinde kullanılır.

```dart
bool isStudent = true;
bool hasLicense = false;

print(isStudent); // true
print(hasLicense); // false
```

**Koşul Örneği:**

```dart
if(isStudent){
  print("Öğrenci girişi başarılı");
} else {
  print("Öğrenci değil");
}
```

---

## 5. **List (Dizi / Array)**

- Sıralı veri koleksiyonu.
- Aynı veya farklı tipte veriler içerebilir.

```dart
List<int> numbers = [1, 2, 3, 4];
List<String> fruits = ["Elma", "Muz", "Armut"];

print(numbers[0]); // 1
print(fruits[2]);  // Armut

numbers.add(5);   // Listeye ekleme
fruits.remove("Muz"); // Silme
```

**Liste üzerinde döngü:**

```dart
for(var fruit in fruits){
  print(fruit);
}
```

---

## 6. **Set**

- Benzersiz (tekrarsız) elemanlar saklar.
- Sıra garanti edilmez.

```dart
Set<int> ids = {1, 2, 3, 3};
print(ids); // {1, 2, 3}  (3 tekrar etmez)
```

---

## 7. **Map (Sözlük / Key-Value)**

- Anahtar-değer çiftleri içerir.
- Veri erişimi anahtar üzerinden olur.

```dart
Map<String, String> user = {
  "name": "TkMatE",
  "city": "Istanbul"
};

print(user["name"]); // TkMatE
print(user["city"]); // Istanbul

user["age"] = "20"; // Yeni eleman ekleme
```

---

## 8. **dynamic**

- Tip güvenliği yoktur, her türlü veri atanabilir.
    
- Gereksiz kullanım önerilmez, sadece esnek durumlarda.
    

```dart
dynamic value = 10;
value = "Merhaba";
value = true;

print(value); // true
```

---

## 9. **var**

- Tip otomatik çıkarılır, ama bir kez atanırsa tip değişmez.

```dart
var name = "TkMatE"; // String olarak atanır
// name = 10; // Hata verir
```

---

## 10. **Null ve Nullable Tipler**

- `?` eklenirse değişken null olabilir.

```dart
String? middleName; // null olabilir
middleName = null;  
print(middleName); // null
```

- Null-aware operatörler:

```dart
String? nickname;
print(nickname ?? "Takma isim yok"); // nickname null ise default yazı
```
