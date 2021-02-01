# Ruby

Ruby öğrenmeye yardımcı kaynaklar
- https://www.tutorialspoint.com/ruby/ruby_overview.htm
- https://www.ruby-lang.org/tr/about/
- http://www.baskent.edu.tr/~tkaracay/etudio/ders/prg/ruby/ch05/200variables.pdf

#### Ruby hakkında genel bilgiler
- ruby dosyalarının uzantısı .rb dir.
- Yorum satırına almak için #
- Birden fazla satırı yorum satırına almak için. 
```
<<-Yorum
--
Yorum

"----"
```
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
- #### Ruby dilinde değişkenler
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
Örnek 
```
class Ogrenci
    @@ogrenci_sayisi=0
    def initialize(no,ad)
        @no=no
        @ad=ad
        @@ogrenci_sayisi+=1
    end

    def display()
        print "Öğrenci no: #@no\n"
        print "Öğrenci ad: #@ad\n" 
    end
   
    def total_ogrenci()
        print "Toplam öğrenci sayısı: #@@ogrenci_sayisi\n"
    end
end


ogrenci1 = Ogrenci.new("181180063","Ali")
ogrenci2 = Ogrenci.new("181180064","Mehmet")

ogrenci1.display()
ogrenci2.display()
ogrenci1.total_ogrenci()
ogrenci2.total_ogrenci()

```
Output
> Öğrenci no: 181180063 <br>
> Öğrenci ad: Ali <br>
> Öğrenci no: 181180064 <br> 
> Öğrenci ad: Mehmet <br>
> Toplam öğrenci sayısı: 2 <br> 
> Toplam öğrenci sayısı: 2 <br>

### Ruby sabitler
Sabitler(Constants) büyük harf ile başlar. Tanımlandığı class ya da modül içinde erişilebilir. Eğer herhangi bir class veya modül içinde tanımlanmamışsa global olarak erişilebilir. Method içinde sabit tanımlanamaz.

### Ruby get set kullanımı

```
class Ogrenci
    
    @name
    def setName(name)
        @name=name
    end

    def getName
        @name
    end

end

ogrenci=Ogrenci.new
ogrenci.setName("xxx")
printf("öğrenci ismi : %s",ogrenci.getName)
```
Output > öğrenci ismi : xxx

### Ruby Paralel Atama
 - Çoklu atamalar mümkün.
 ```
 x,y,z=1,2,3
 ```
 x y x değerlerine sırasıyla 1 2 3 değerlerini atıyor. Eğer karşısına 3 değerden az yazsaydık boşta kalanlar nil olacaktı.Örneğin x,y,z=1,2 için x=1,y=2 ve z=nil.
 
 - aynı zamanda değer takas etmek için ayrı bir değişkene ihtiyacımız yok.
 ```
 x,y=y,x
 ```
 x ve ynin değerlerini takas ettirdik.
 
 ### if - else kullanımı 

- İf ifadesi ile yapılması istenen şeyler yeni bir satır, noktalı virgül ya da "then" ifadelesi ile ayrılır.
 ```
 condition=true 
 if true then print "xxx"
 end
 ```
 İf - else kullanımı. 
```
condition=5
if condition
    print "Koşul false ya da nil ise false, diğer tüm durumlar true"
elsif condition
    print "elsif olarak yazılyor. else if değil."
else 
    print "kaçta if else olsun fark etmez. En sona bir tane end geliyor."
end
```
Output: > Koşul false ya da nil ise false, diğer tüm durumlar true
<br>
Aynı zamanda tek satırda da kullanabiliriz. *end kullanılmıyor bu durumda*
 > kod if koşul 
```
condition=5
print "xxx" if condition 
```
output: > xxx

- Unless kullanımı yukarıdakinin aynısı ancak rubyde unless ile birlikte elsif kullanılamıyor.Yani aşağıdaki hatalı. Ayrıca unless kullanımı önerilmiyor.
```
unless true
  puts "one"
elsif true
  puts "two"
else
  puts "three"
end

```
Output: > Compiler error.

### Case kullanımı

- "===" kapsama operatorü ile kullanılır.
Kapsama operatorü boolean olarak geri dönüş verir.

```
 (1..5) === 3             # => true
 (1..5) === 6             # => false

  Integer === 42          # => true
  Integer === 'bmt' # => false
```

case expression
[when expression [, expression ...] [then]
   code ]...
[else
   code ]
end

When li koşullardan hiçbirini sağlamazsa else'e girer.
Örnek:
```
değer=5
case değer
when 0..2
    puts "0-2 arasında"
when 3..7
    puts "3-7 arasında"
else
    puts "7den büyük"
end
```
Yukarıdaki ifadenin if-else ile yazılımı
```
değer=5
if (0..2)===değer
    puts "0-2 arasında"
elsif (3..7)===değer
    puts "3-7 arasında"
else
    puts "7den büyük"
end
```







