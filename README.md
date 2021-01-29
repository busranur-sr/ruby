# ruby

Ruby öğrenmeye yardımcı kaynaklar
- https://www.tutorialspoint.com/ruby/ruby_overview.htm
- https://www.ruby-lang.org/tr/about/
- http://www.baskent.edu.tr/~tkaracay/etudio/ders/prg/ruby/ch05/200variables.pdf

#### Ruby hakkında genel bilgiler
- ruby dosyalarının uzantısı .rb dir.
- Ruby saf bir nesne yönelimli programlama dilidir ki bu aşağıdaki özellikleri sağlıyor demektir.
  - Encapsulation
  - Inheritance
  - Polymorphism
  - Abstraction
  - Data Hiding
  - Kullanıcının tanımladığı tüm veri tipleri bir objedir
  - Önceden tanımlanan tüm veri tipleri bir objedir
  (Yani int, double, float gibi ilkel veri tipleri içermiyor. Örnek olarak java saf nesne yönemli programla dili değildir.
   
  Kaynak(https://www.c-sharpcorner.com/blogs/full-object-oriented-language-vs-pure-object-oriented-language1)

#### Ruby dilinde Class ve objeler
- Rubyde classlar "class" ile başlar ve "end" ile biter. Ayrıca classınızın adı büyük harf ile başlamalıdır.
```
class MyClass
end
```
- Obje yaratmak için "new" kullanıyoruz.
```
obje_ismim = MyClass.new 
```
- Ruby dilinde fonksiyonlar method olarak isimlendirililer. Methodlar "def" ile başlar ve "end" ile biterler. Method isimlerinin küçük harf ile başlaması tercih edilir.
```
class Class1 
    def method1
        puts "bmt"    
    end
end

my=Class1.new
my.method1
```
Output > bmt
- Eğer objeni parametreli olarak yaratıcaksan classının içinde "initialize" methodunu kullanmalısın. (Constructor) 
- ######Ruby dilinde değişkenler
  - Yerel değişkenler ( Local Variables ) : Method içinde tanımlanan ve kullanılan değişkenlerlir. Method dışında kullanılamazlar. Küçük harf ile ya da '_' ile başlar.
  - Anlık değişkenler ( Instance Variables ) : Yalnızca üretilen nesne içinde geçerlidir. Methodlar arasında kullanılabilen değişkenlerdir. Yani objeden objeye değişkenlik gösterir. İsimlendirmesi '@' ile başlar.
  - Sınıf değişkenleri ( Class Variables ) : Sınıf değişkenleri, değişkenin tanımlandığı sınıfta ve onun bütün altsınıflarında (oğul) ve modüllerinde geçerlidir. Yani class'a ait bir değişkendir. İsimlendirmesi '@@' ile başlar.
  - Global Variables : Global değişken, bütün programın her yerinden erişilebilecek değişkendir. Global değişken adları $ simgesiyle başlar. Değer atanmamış değişkenlerin
öntanımlı değeri nil’dir. Değer atanmamış değişkenler programda kullanılırsa, derleyici uyarı yollar. İsimlendirmesi '$' ile başlar.
 
Örnek
```
class Ogrenci
    @@ogrenci_sayisi=0
    def initialize(no,ad)
        @no=no
        @ad=ad
    end
end

ogrenci1 = Ogrenci.new("181180063","Ali")
ogrenci2 = Ogrenci.new("181180064","Mehmet")
```
Bu durumda initialize methodunun parametre olarak aldığı no ve ad değişkenleri local değişkenler oluyor ve initialize methodu dışında kullanılamıyorlar. Bu methodun içinde local değişkeler ; @ad,@no Instance değişkenlerine atanıyor. Ayrıca @@@ogrenci_sayisi değişkeni Class değişkeni olup Ogrenci classından yaratılan tüm objelerde kullanılabilir.

> Rubyde değişkenlere ulaşmak için '#' kullanıyoruz.

### Ruby sabitler
Sabitler(Constants) büyük harf ile başlar. Tanımlandığı class ya da modül içinde erişilebilir. Eğer herhangi bir class veya modül içinde tanımlanmamışsa global olarak erişilebilir. Method içinde sabit tanımlanamaz.

### Ruby değişkenimsiler(Pseudo-Variables)
- self 

kaynak (https://www.rubyguides.com/2020/04/self-in-ruby/)
#### Ruby 

