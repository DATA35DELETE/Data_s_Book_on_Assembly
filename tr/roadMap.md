# Data's Book on Assembly
 
## Assembly
 
### Ön Söz
- Ben kimim?
- Bu Data's Book on Assembly nedir?
- Bu dokümantasyon ne öğretecek?
 
---
 
### Assembly : Giriş
- **Assembly Nedir?**: Tanım. Kullanım Alanları. Neden Assembly?
  - **Kısa Tarihçesi**: İlk Assembler'lardan Günümüze.
  - **Makine Kodu ile İlişkisi**: Assembly → Makine Kodu. Birebir Karşılık.
  - **High-Level Diller ile Karşılaştırma**: Tablo Halinde. Avantajlar ve Dezavantajlar.
  - **Kullanım Alanları**: Firmware. OS Kernel. Oyun Optimizasyonu. Tersine Mühendislik. Gömülü Sistemler.
- **CPU ve Bellek Temelleri**:
  - **CPU Nedir?**: Tanım. ALU. Control Unit. Registers. Genel Bakış.
  - **Register Nedir?**: Tanım. Neden Hızlı? Kullanım Senaryoları.
  - **Bellek (RAM) Nedir?**: Tanım. CPU ile İletişim. Adres Kavramı.
  - **Bus Sistemi**: Data Bus. Address Bus. Control Bus. Tanım.
  - **Clock Cycle**: Tanım. Fetch-Decode-Execute Döngüsü.
- **Assembly Türleri**:
  - **x86 (32-bit)**: Tanım. IA-32 Mimarisi. Kullanım.
  - **x86-64 (64-bit)**: Tanım. AMD64. En Yaygın Masa Üstü Mimarisi.
  - **ARM**: Tanım. Mobil ve Gömülü Sistemler. Farkı.
  - **Bu Dokümantasyonda**: x86-64 (Linux). NASM Assembler.
- **Araçları Kurma**:
  - **NASM Kurulumu**: NASM Nedir? Kurulum Adımları. Örnek.
  - **GDB Kurulumu**: Hata Ayıklama Aracı. Kurulum.
  - **ld (Linker)**: Tanım. Kullanım.
  - **IDE / Editör Seçimi**: VS Code. asm Eklentisi.
- **İlk Program**: Hello World.
  - **Derleme**: `nasm -f elf64`. Örnek.
  - **Linkleme**: `ld`. Örnek.
  - **Çalıştırma**: `./program`. Örnek.
 
---
 
### Assembly : Temel Kavramlar
- **Sayı Sistemleri**: Neden Önemli?
  - **Binary (İkili)**: Tanım. Bit ve Byte. Örnek.
  - **Hexadecimal (Onaltılı)**: Tanım. Neden Kullanılır? Binary ile Dönüşüm. Örnek.
  - **Octal (Sekizli)**: Tanım. Kısa Özet.
  - **Dönüşümler**: Binary ↔ Decimal ↔ Hex. Tablo Halinde.
- **Bit İşlemleri**: Tanım. Kullanım Senaryoları.
  - **AND**: Tanım. Örnek.
  - **OR**: Tanım. Örnek.
  - **XOR**: Tanım. Örnek.
  - **NOT**: Tanım. Örnek.
  - **SHL / SHR (Shift)**: Tanım. Çarpma/Bölme Kısayolu. Örnek.
- **İşaretli ve İşaretsiz Sayılar**: Tanım. Two's Complement. Örnek.
- **Endianness**: Little-Endian vs Big-Endian. x86'da Durum. Örnek.
- **Veri Boyutları**: Bit. Byte. Word (2B). Dword (4B). Qword (8B). Tablo Halinde.
 
---
 
### Assembly : Registerlar
- **Register Nedir?**: Tanım. RAM ile Farkı. Neden Kullanılır?
- **Genel Amaçlı Registerlar (x86-64)**:
  - **RAX, EAX, AX, AL**: Tanım. 64/32/16/8-bit Alt Bölümler. Örnek.
  - **RBX, RCX, RDX**: Tanım. Örnek.
  - **RSI ve RDI**: Tanım. Source ve Destination. Örnek.
  - **RSP**: Stack Pointer. Tanım. Örnek.
  - **RBP**: Base Pointer. Stack Frame. Tanım. Örnek.
  - **R8 - R15**: Tanım. x86-64 Ek Registerlar. Örnek.
  > Tablo Halinde: Tüm Registerlar ve Alt Bölümleri
- **Özel Registerlar**:
  - **RIP (Instruction Pointer)**: Tanım. Program Akışı. Örnek.
  - **RFLAGS**: Tanım. Flag Bitleri. Kullanım Senaryosu.
    - **ZF (Zero Flag)**: Tanım. Örnek.
    - **CF (Carry Flag)**: Tanım. Örnek.
    - **SF (Sign Flag)**: Tanım. Örnek.
    - **OF (Overflow Flag)**: Tanım. Örnek.
- **Segment Registerlar**: CS, DS, SS, ES, FS, GS. Kısa Tanım.
- **XMM / YMM Registerlar**: Tanım. SIMD. Kısa Özet.
 
---
 
### Assembly : Syntax ve Yapı
- **Assembly Syntax Türleri**:
  - **Intel Syntax**: Tanım. `mov dst, src`. Bu dokümantasyonda kullanılan.
  - **AT&T Syntax**: Tanım. `mov src, dst`. GAS Assembler. Farklar.
  > Tablo Halinde Karşılaştırma
- **NASM Program Yapısı**: Bölümler. Tanım. Örnek.
  - **section .data**: Başlatılmış Veri. Tanım. Örnek.
  - **section .bss**: Başlatılmamış Veri. Tanım. Örnek.
  - **section .text**: Kod Bölümü. `global _start`. Tanım. Örnek.
- **Etiketler (Labels)**: Tanım. Adres Göstergesi. Örnek.
- **Yorum Satırı**: `;`. Tanım. Örnek.
- **Veri Tanımlama Direktifleri**:
  - **db (Define Byte)**: Tanım. Örnek.
  - **dw (Define Word)**: Tanım. Örnek.
  - **dd (Define Dword)**: Tanım. Örnek.
  - **dq (Define Qword)**: Tanım. Örnek.
  - **resb / resw / resd / resq**: Tanım. .bss'de Kullanım. Örnek.
- **Sabitler**: `equ`. Tanım. Örnek.
 
---
 
### Assembly : Veri Hareketi
- **mov Komutu**: Tanım. En Temel Komut. Sözdizimi. Örnek.
  - **Register ← Sabit**: Örnek.
  - **Register ← Register**: Örnek.
  - **Register ← Bellek**: Örnek.
  - **Bellek ← Register**: Örnek.
- **Bellek Adresleme Modları**: Tanım.
  - **Immediate**: Doğrudan Değer. Örnek.
  - **Register**: Register İçeriği. Örnek.
  - **Direct**: Sabit Adres. `[adres]`. Örnek.
  - **Indirect**: `[register]`. Örnek.
  - **Base + Displacement**: `[register + offset]`. Örnek.
  - **Base + Index**: `[base + index * scale + offset]`. Örnek.
- **lea Komutu**: Tanım. mov ile Farkı. Adres Hesaplama. Örnek.
- **xchg Komutu**: Tanım. İki Değeri Değiştirme. Örnek.
- **movzx ve movsx**: Tanım. Zero-Extend. Sign-Extend. Örnek.
 
---
 
### Assembly : Aritmetik İşlemler
- **add**: Tanım. Sözdizimi. Flag Etkisi. Örnek.
- **sub**: Tanım. Sözdizimi. Flag Etkisi. Örnek.
- **inc ve dec**: Tanım. +1 ve -1. Örnek.
- **mul**: İşaretsiz Çarpma. Tanım. RAX ile İlişki. Örnek.
- **imul**: İşaretli Çarpma. Tanım. Örnek.
- **div**: İşaretsiz Bölme. Tanım. RAX / RDX İlişkisi. Örnek.
- **idiv**: İşaretli Bölme. Tanım. Örnek.
- **neg**: Tanım. Two's Complement. Örnek.
- **Taşma (Overflow) ve Elde (Carry)**: Tanım. CF ve OF Bayrakları. Örnek.
- **adc (Add with Carry)**: Tanım. Büyük Sayı Toplama. Örnek.
 
---
 
### Assembly : Karşılaştırma ve Atlamalar
- **cmp Komutu**: Tanım. sub ile Farkı. Flag Etkisi. Örnek.
- **test Komutu**: Tanım. AND ile Farkı. Örnek.
- **Koşulsuz Atlama**:
  - **jmp**: Tanım. Sözdizimi. Örnek.
- **Koşullu Atlamalar**: Tanım. Flag'lere Göre. Tablo Halinde.
  - **je / jne**: Eşit / Eşit Değil. ZF. Örnek.
  - **jg / jl**: Büyük / Küçük (İşaretli). Örnek.
  - **jge / jle**: Büyük-Eşit / Küçük-Eşit (İşaretli). Örnek.
  - **ja / jb**: Büyük / Küçük (İşaretsiz). Örnek.
  - **jz / jnz**: Zero / Non-Zero. Örnek.
  - **jc / jnc**: Carry / No Carry. Örnek.
  - **jo / jno**: Overflow / No Overflow. Örnek.
- **If-Else Yapısı**: Assembly Karşılığı. Örnek.
- **Döngü Yapıları**:
  - **while Döngüsü**: Assembly Karşılığı. Örnek.
  - **for Döngüsü**: Assembly Karşılığı. Örnek.
  - **loop Komutu**: Tanım. RCX ile Kullanım. Örnek.
 
---
 
### Assembly : Stack (Yığın)
- **Stack Nedir?**: Tanım. LIFO. Bellek Düzeni. RSP ile İlişki.
- **Stack Yönü**: Aşağı Büyüme. Tanım. Görselleştirme.
- **push Komutu**: Tanım. RSP Değişimi. Örnek.
- **pop Komutu**: Tanım. RSP Değişimi. Örnek.
- **Stack Kullanım Senaryoları**: Geçici Veri Saklama. Fonksiyon Çağrısı. Örnek.
- **Stack Taşması (Stack Overflow)**: Tanım. Nasıl Oluşur? Örnek.
- **Stack Hizalaması (Alignment)**: Tanım. 16-byte Hizalama. Neden Önemli? Örnek.
 
---
 
### Assembly : Fonksiyonlar ve Çağırma Kuralları
- **Fonksiyon Nedir?**: Assembly'de Fonksiyon Kavramı. Label ile Tanım. Örnek.
- **call ve ret**:
  - **call**: Tanım. Return Adresini Stack'e Basma. Örnek.
  - **ret**: Tanım. Stack'ten Adres Alma. Örnek.
- **Çağırma Kuralları (Calling Conventions)**: Tanım. Neden Önemli?
  - **System V AMD64 (Linux/macOS)**: Parametre Registerları. RDI, RSI, RDX, RCX, R8, R9. Dönüş: RAX. Örnek.
  - **Microsoft x64 (Windows)**: Parametre Registerları. RCX, RDX, R8, R9. Farklar. Örnek.
  > Tablo Halinde Karşılaştırma
- **Caller-Saved ve Callee-Saved Registerlar**: Tanım. Tablo Halinde. Örnek.
- **Stack Frame**:
  - **Prologue**: `push rbp`. `mov rbp, rsp`. Tanım. Örnek.
  - **Epilogue**: `pop rbp`. `ret`. Tanım. Örnek.
- **Yerel Değişkenler**: Stack'te Alan Açma. `sub rsp, N`. Örnek.
- **Özyinelemeli Fonksiyon (Recursion)**: Tanım. Factorial Örneği.
 
---
 
### Assembly : Sistem Çağrıları (Syscall)
- **Syscall Nedir?**: Tanım. OS ile İletişim. Kullanım Senaryoları.
- **Linux x86-64 Syscall Mekanizması**: Tanım. `syscall` Komutu. Örnek.
  - **RAX**: Syscall Numarası. Tanım.
  - **RDI, RSI, RDX, R10, R8, R9**: Parametreler. Örnek.
- **Temel Syscall'lar**:
  - **sys_write (1)**: Tanım. stdout'a Yazma. Örnek.
  - **sys_read (0)**: Tanım. stdin'den Okuma. Örnek.
  - **sys_exit (60)**: Tanım. Programı Sonlandırma. Örnek.
  - **sys_open (2)**: Tanım. Dosya Açma. Örnek.
  - **sys_close (3)**: Tanım. Dosya Kapama. Örnek.
  - **sys_mmap (9)**: Tanım. Bellek Tahsisi. Örnek.
  > Sık Kullanılan Syscall Tablosu
- **Hata Kontrolü**: Dönüş Değeri. Negatif = Hata. Örnek.
 
---
 
### Assembly : Bellek Yönetimi
- **Bellek Düzeni**: Programın RAM'deki Yapısı. Görselleştirme.
  - **Text Segment**: Kod. Salt Okunur. Tanım.
  - **Data Segment**: Başlatılmış Veriler. `.data`. Tanım.
  - **BSS Segment**: Başlatılmamış Veriler. `.bss`. Tanım.
  - **Stack**: Otomatik Ömürlü. LIFO. Tanım.
  - **Heap**: Dinamik Bellek. `mmap` ile Tahsis. Tanım.
- **Doğrudan Bellek Erişimi**: `[adres]`. Örnek.
- **Dizi İşlemleri**: Tanım. Base + Index ile Erişim. Örnek.
- **String İşlemleri**:
  - **movsb / movsw / movsd / movsq**: Tanım. Bellek Kopyalama. Örnek.
  - **rep Prefix**: Tanım. Tekrarlı İşlem. `rep movsb`. Örnek.
  - **stosb**: Tanım. Bellek Doldurma. Örnek.
  - **scasb**: Tanım. Bellek Arama. Örnek.
- **Dinamik Bellek**: `sys_mmap` ile Heap Tahsisi. Tanım. Örnek.
 
---
 
### Assembly : C ile Birlikte Kullanım
- **Neden C ile Birlikte Kullanılır?**: Tanım. Kullanım Senaryoları.
- **C'den Assembly Fonksiyonu Çağırma**:
  - **extern Bildirimi**: Tanım. Örnek.
  - **Derleme ve Linkleme**: `nasm` + `gcc`. Örnek.
- **Assembly'den C Fonksiyonu Çağırma**:
  - **extern ile C Fonksiyonu**: `printf`, `malloc`. Tanım. Örnek.
- **Calling Convention Uyumu**: Tanım. Parametre Geçirme. Örnek.
- **Inline Assembly (GCC)**:
  - **`__asm__` Bloğu**: Tanım. Sözdizimi. Örnek.
  - **Constraint'ler**: Giriş/Çıkış Operandları. `"r"`, `"m"`. Örnek.
  - **Volatile**: Tanım. Optimizasyonu Engelleme. Örnek.
- **Derlenen C Kodunu İnceleme**: `gcc -S`. Assembly Çıktısı Okuma. Örnek.
 
---
 
### Assembly : Hata Ayıklama (Debugging)
- **GDB ile Assembly Debug**: Tanım. Kurulum. Başlatma. Örnek.
  - **layout asm**: Assembly Görünümü. Örnek.
  - **layout regs**: Register Görünümü. Örnek.
  - **break (b)**: Breakpoint Koyma. Örnek.
  - **run (r)**: Programı Çalıştırma. Örnek.
  - **stepi (si)**: Bir Komut İlerle. Örnek.
  - **nexti (ni)**: Fonksiyon Atla. Örnek.
  - **info registers**: Tüm Registerları Göster. Örnek.
  - **x Komutu**: Bellek İnceleme. `x/8xb`. Örnek.
  - **print (p)**: Değer Yazdırma. Örnek.
- **strace**: Tanım. Syscall Takibi. Örnek.
- **objdump**: Tanım. Binary İnceleme. `objdump -d`. Örnek.
- **readelf**: Tanım. ELF Başlığı İnceleme. Örnek.
 
---
 
### Assembly : Önişlemci ve Makrolar (NASM)
- **NASM Direktifleri**: Tanım. Genel Bakış.
- **%define**: Sabit Tanımlama. Örnek.
- **%macro / %endmacro**: Makro Tanımlama. Parametreli Makro. Örnek.
- **%if / %elif / %else / %endif**: Koşullu Derleme. Örnek.
- **%include**: Harici Dosya Dahil Etme. Örnek.
- **Çoklu Dosya Projesi**: Tanım. `global` ve `extern`. Linkleme. Örnek.
 
---
 
### Assembly : Pratik Örnekler
- **Sayı Yazdırma**: Integer'ı ASCII'ye Çevirme ve Yazdırma. Örnek.
- **Kullanıcıdan Input Alma**: `sys_read` ile. Örnek.
- **String Uzunluğu Hesaplama**: Döngü ile. Örnek.
- **İki Sayıyı Toplama**: Fonksiyon Yazma. Örnek.
- **Dizi Toplamı**: Loop ile Dizi Elemanlarını Toplama. Örnek.
- **Fibonacci**: Iteratif ve Recursive. Örnek.
- **Basit Hesap Makinesi**: Kullanıcıdan İki Sayı Al. İşlem Seç. Sonuç Göster. Örnek.
 
---
 
### Sonsöz
- **Bu Dokümantasyonda Ne Öğrendik**
- **İlerki Projeler**
- **Diğer Data's Books Dökümantasyonları**
- **Özel Teşekkürler**
 
---