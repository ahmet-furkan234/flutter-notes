
# 🟦 Encapsulation (Kapsülleme)

**Tanım:**  
Encapsulation, bir sınıfın **veri ve metodlarını dışarıya kontrollü bir şekilde açmasıdır**.

- Alanlar (`fields`) **private** yapılabilir.
- Sadece gerekli metodlar (getter/setter) ile dışarıya veri sunulur.

Dart’ta **private** yapmak için **_ (underscore)** kullanılır.

---

## 🔹 1. Private Field Örneği

```dart
class BankAccount {
  String _accountNumber; // private
  double _balance = 0;   // private

  BankAccount(this._accountNumber, this._balance);

  // getter
  double get balance => _balance;

  // deposit method
  void deposit(double amount) {
    if (amount > 0) {
      _balance += amount;
      print("Hesaba $amount TL yatırıldı. Yeni bakiye: $_balance");
    } else {
      print("Geçersiz miktar!");
    }
  }

  // withdraw method
  void withdraw(double amount) {
    if (amount > 0 && amount <= _balance) {
      _balance -= amount;
      print("Hesaptan $amount TL çekildi. Yeni bakiye: $_balance");
    } else {
      print("Yetersiz bakiye veya geçersiz miktar!");
    }
  }
}

void main() {
  BankAccount account = BankAccount("123456", 1000);
  
  print(account.balance); // 1000 ✅ getter ile erişim
  account.deposit(500);   // Hesaba 500 TL yatırıldı
  account.withdraw(200);  // Hesaptan 200 TL çekildi
  // print(account._balance); // ❌ HATA! private field
}
```

📌 Açıklama:

- `_balance` ve `_accountNumber` private.
- Dışarıdan **direkt erişim yok**.
- Getter/setter veya metodlar ile kontrollü erişim sağlanıyor.

---

## 🔹 2. Getter ve Setter ile Kapsülleme

```dart
class Person {
  String _name = "";
  int _age = 0;

  // Getter
  String get name => _name;
  int get age => _age;

  // Setter
  set name(String value) {
    if (value.isNotEmpty) _name = value;
  }

  set age(int value) {
    if (value >= 0) _age = value;
  }
}

void main() {
  Person p = Person();
  p.name = "TkMatE";
  p.age = 25;

  print(p.name); // TkMatE
  print(p.age);  // 25
}
```

📌 Getter/setter ile:

- Veriyi **kontrollü şekilde değiştirebilir** veya doğrulayabilirsin.
- Direct `_field` erişimi engellenir.

---

## 🔹 3. Neden Encapsulation Önemli?

1. **Güvenlik:** Önemli verilere dışarıdan kontrolsüz erişim yok.
2. **Kontrol:** Değerlerin doğruluğunu metodlarda kontrol edebilirsin.
3. **Bakım Kolaylığı:** Sınıfın iç yapısı değişse bile dışarıya API sabit kalır.
4. **OOP prensiplerine uygunluk:** Abstraction ve polymorphism ile birlikte kullanılır.

---

## 🔹 4. Özet

- `_field` → private alan
- Getter → veri okuma
- Setter → veri yazma + kontrol
- Encapsulation → sınıfın içini **dışa kapatıp kontrollü açmak**
