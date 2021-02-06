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

> Ruby değerlerini string içinde kullanabilmek için #{ } kullanıyoruz. 
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
    print "kaç tane if else olduğu fark etmez. En sona bir tane end geliyor."
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

"case" "when" "end" ifadeleri ile kullanılır. When li koşullardan hiçbirini sağlamazsa else'e girer.
```
ifade="bmt"
case ifade
when "bmt"
    puts "x"
when "gazi"
    puts "xx"
else
    puts "xxx"
end
```
- "===" kapsama operatorü ile de kullanılır.
Kapsama operatorü boolean olarak geri dönüş verir.

```
 (1..5) === 3             # => true
 (1..5) === 6             # => false

  Integer === 42          # => true
  Integer === 'bmt' # => false
```

case expression
[when expression [, expression ...] [then] <br>
   code ]... <br>
[else<br>
   code ] <br>
end

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

### Döngüler

- #### While döngüsü

while koşul [do] <br>
  ---yapılacaklar--- <br>
 end <br>
 
"do" ifadesi yerine "\" , ";" kullanabilir ya da yeni satıra geçebiliriz.

Örnek
```
x=1
y=5
while x<y 
    print x
    x+=1
end
```
Output: > 1234
 - while döngüsünü daha farklı şekilde de kullanabiliriz
 
 > code while koşul
 <br>
 ya da
 <br>
 > begin <br>
 >  -yapılacaklar- <br>
 >  end while koşul

- Yukarıdaki durumda en başta koşul değerlendirilmeden bir kere çalışır daha sonra koşul değerlendirilip devam eder.

Örnek:
```
x=1
y=5
begin 
    print x
    x+=1
end while x>y
```
Output: > 1
 
- *until ifadesi while ile aynı mantığa sahiptir. Tek fark *koşulu sağlamadığında* çalışır.

- **for kullanımı**
```
for $i in 0..5
    puts "#$i"
end
(0..5).each do |j|
    puts "#{j}"  "->local verilere "#"den sonra süslü parantez içinde erişiyoruz. "
end
```
- İkiside aynı şeyi yapıyor
Output:
> 0 \
> 1 \
> 2 \
> 3 \
> 4 \
> 5 

- break : döngüyü sonlandırıyor. 
- next  : bir sonraki döngüye geçiyor. 
- redo  : döngünün bulunduğu konumu tekrar ediyor. Koşulu kontrol etmeden 
- retry : baştan başlatır. //ruby 1.9 dan beri döngülerde kullanılamıyor. // ileride kullanımını göreceğiz.
Örnek:
```
for i in 0..10
    if(i%3==0)
        next; 
    end
    break if (8..9)===i 
    puts "i: #{i}" 
end
```
Output:
> i: 1 \
> i: 2 \
> i: 4 \
> i: 5 \
> i: 7

Örnek:
```
(0..5).each do |i|
  puts "Value: #{i}"
  redo if i > 2
end
```
Output: 
> Value: 0 \
> Value: 1 \
> Value: 2 \
> Value: 3 \
> Value: 3 \
> Value: 3 \
> .... sonsuz döngüye girdi.
          
<br>
Kaynak: (https://rubyquicktips.com/post/1122838559/redo-vs-retry#:~:text=redo%20and%20retry%20are%20both,whole%20loop%20from%20the%20start.)

## Ruby Methodlar

- Diğer dillerdeki fonksiyonlardan çok da bir farkları yok.
- Küçük harf ile başlamalılar. Diğer türlü ruby methodları sabit(constant) sanabilir.
- def method_adi(x,y) -> tabi eğer parametreli yapmak istiyorsak \
  --- \
  end
- Ayrıca ruby dilinde default parametre belirleyebiliyoruz. Bu sayede parametreli methodlar parametresiz çağırıldığında değişkenlerin alabileceği değerler oluyor.
```
def method1(x=0,y=0)
    puts "x: #{x} y: #{y}"
end

method1 
method1 5 , 10
```
Output:
> x: 0 y: 0 \
> x: 5 y: 10

- **return etme** rubyde methodun son satırıdaki değer return edilir.
```
def method1(x=0,y=0)
    puts "x: #{x} y: #{y}"
    k=0
end

a=method1 
method1 5 , 10

puts a "0 yazdırır"
```
- Aynı zamanda return edilecek değeri bizde belirleyebiliyoruz. Eğer sadece return dersek nil döndürür. return x, x döndürür zaten.
- Birden fazla değeri return ettiğimizde ( return 1 , 2 ) bu değerleri içeren dizi return edilir.
- Değişken parametre sayısı belirlenebilir. 
```
def değişken_parametreli_method(*prm)
    puts "Parametre sayısı #{prm.length}"
    for i in 0...prm.length
       puts "veriler: #{prm[i]}"
    end
    
end

değişken_parametreli_method "x","y","z"
değişken_parametreli_method "1"
```
Output: 
> Parametre sayısı 3 \
> veriler: x \
> veriler: y \
> veriler: z \
> Parametre sayısı 1 \
> veriler: 1

*kaç tane parametre girilirse ona uygun dizi tanımlanıp değerler içine atılıyor.*

- Bir method class dışında tanımlanırsa varsayılan olarak private, class içinde tanımlanırsa varsayılan olarak public tanımlanır. Class içindeki methodlara ulaşmak için ilk önce classdan bir obje yaratıp sonra bu obje ile methoda ulaştığımızı biliyoruz. Ruby dilinde classı başlatmadan yani obje yaratmadan class içindeki methoda ulaşmak mümkün. Methodun adını "class_adı.method_adi"  yapmamız gerekiyor sadece.

```
class Class1
    def Class1.ekrana_yazdır
        puts "xxx"
    end 
end 

Class1.ekrana_yazdır
```
Output:
> xxx

## Ruby Bloklar

Örnek: 
(https://www.buraksenyurt.com/post/ruby-kod-parcaciklari-10-yield-ve-block-kullanimi)-
- Bir Block ile değişkene veya nesneye atayamadığımız kod parçalarını işaret edebilir ve bu isimsiz kod parçalarını metodlara parametre olarak taşıyabiliriz. Aslında methodları kod parçacıkları ile çağırmak için kullanıır diyebiliriz.
- Block ismi ile methodun isminin aynı olması gerekiyor.
- "yield" anahtar kelimesi kullanılır. blockları bu ifade ile çağırıyoruz.
```
def deneme
    puts "Methodun içindesin"
    yield 
    puts "Tekrardan methodunun içindesin"
    yield
end

deneme { 
    puts "block içindesin"
}
```
Output:
> Methodun içindesin \
> block içindesin \
> Tekrardan methodunun içindesin \
> block içindesin 

- Blocklar parametre alabilir. Bunun  için parametreleri "| |" içinde tanımlamız gerekmektedir. Ayrıca parametre değerleri yield yanı yazılır.
```
def deneme
    puts "Methodun içindesin"
    yield 5,10
    puts "Tekrardan methodunun içindesin"
end

deneme { 
    |x,y|
    puts "block içindesin "
    puts "x: #{x} y: #{y}"
}
```
Output: 
> Methodun içindesin \
> block içindesin \
> x: 5 y: 10 \
> Tekrardan methodunun içindesin

- **"BEGIN" ve "END" blockları** 
  - Dosya çalıştırıldığında ilk çalışan kısım begin bloclakları ve en son çalışan kısım end blocklarıdır. Aşağıdaki örnekten daha iyi anlaşılabilir.
  ```
  BEGIN { 
   # BEGIN block code 
   puts "BEGIN code block"
  } 

  END { 
   # END block code 
   puts "END code block"
   }
   # MAIN block code 
   puts "MAIN code block"
  ```
Output: 
> BEGIN code block \
> MAIN code block \
> END code block

## Ruby Modüller 
- kaynak (http://www.belgeler.org/uygulamalar/ruby/ruby-ug-modules.html)

- Classlara benzerler ancak örnek ve alt sınıfı oluşturulamaz. 
- module .. end şeklinde tanımlanırlar.
- modül adları büyük harf ile başlamalıdır.
- İki çeşit kullanımı yaygındır.
  - Birinci kullanım nedeni ilişkili method ve sabitleri bir arada toplamaktır. Örnek -> Math modülü
    - Modül içindeki methodlar class methodu gibi tanımlanır. ( yani modül_adi.method_adi )
    - Modül içindeki sabitlere ulaşabilmek "::" kullanmız gerekmektedir. Örnek
     ```
     x= Math::PI
     puts x
     ```
     Output: 
     > 3.141592653589793
  
      ```
      module Benim_modülüm
        Sabit=5.7
        def Benim_modülüm.toplama(x)
        sonuc=x+Sabit
        end

        def Benim_modülüm.çarpma(x)
        sonuc=x*Sabit
        end
      end

      puts Benim_modülüm::Sabit
      puts Benim_modülüm.toplama(7)
      ```
      Output:
      > 5.7 \
      > 12.7
    
    - modülün içindeki methodlara direk ulaşmak istiyorsak "include" etmemiz gerekmektedir. Bu sayede class methodu kullanmamıza gerek kalmaz.
    ```
    module Benim_modülüm
    Sabit=5.7
    def toplama(x)
    sonuc=x+Sabit
    end

    def çarpma(x)
    sonuc=x*Sabit
    end
    end

    include Benim_modülüm
    puts Sabit
    puts toplama(7)
    ```
  
   - İkinci kullanım şekli ise karışım (mixin) dir. Ruby çoğlu mirası ( multiple inheritance ) desteklemiyor. Ancak bunu modüller bunu yapabilmemize olarak sağlıyor. 
   Örnekten daha kolay anlaşılabiir.
   ```
   module A
    def method
        puts "xxx"
    end
   end 

   module B
    def method2
        puts "yyy"
    end
   end

   class C
    include A
    include B
   end

   my=C.new
   my.method
   my.method2
   
   ```
   Output:
   > xxx \
   > yyy
   
   ### Ruby "include" ifadesi
    (daha detaylı incelenmesi gerek.)
    - https://stackoverflow.com/questions/318144/what-is-the-difference-between-include-and-require-in-ruby  
    - Modülün adı kullanarak include ederiz . Dosyanın adıyla değil.
    - Genelde koddaki tekrarlamadan kurtulmak için kullanılır.
    
   ### Ruby "require" ifadesi 
     (daha detaylı incelenmesi gerek.)
     - https://stackoverflow.com/questions/318144/what-is-the-difference-between-include-and-require-in-ruby  
     - Diğer dillerde include ne yapıyorsa ruby de  require ona yapar.
     - Modülün bulunduğu dosyanın adıyla require ederiz. Modül adıyla değil.
     - Amacımız kalıtım sağlamak değilse direk modüle ihtiyacımız varsa kullanıyoruz.
    
    
  ## Ruby Stringler
 
 - Ruby değerlerini string içinde kullanabilmek için #{ } kullanıyoruz. 
 ```
 x,y=5,8
 benim_Stringim = "İstediğim değer : #{x*y} "
 puts benim_Stringim
 ```
 Output:
 > İstediğim değer : 40 
 - String methodları kullanabilmek için elimide String objesi olmalıdır. 
 - String methodları (https://www.tutorialspoint.com/ruby/ruby_strings.htm) \
                     (https://towardsdatascience.com/17-useful-ruby-string-methods-to-clean-and-format-your-data-9c9147ff87b9)
                     
             
 - Bazi String methodlarını inceleyeceğiz ancak yukarıdaki adrese göz gezdirilmesi önerilir.
 ```
 benim_Stringim = String.new("Tahirle Zühre Meselesi") #normal de tanımlanabilir.
 puts benim_Stringim
 puts benim_Stringim.downcase # Tüm karakteri küçük yapar.
 puts benim_Stringim.chars # Stringi charlara ayırır
 puts benim_Stringim.length #String uzunluğunu döndürür
 puts benim_Stringim.include?("i") # true ya da false döndürür.
 puts benim_Stringim.count("i") # verilen değeri kaç tane içerdiğini döndürür.
 puts benim_Stringim.reverse # String'i ters döndürür.
 puts benim_Stringim.split # verilen değeri baz alarak Stringi ayırır. 
  ```
 Output:
 > Tahirle Zühre Meselesi \
 > tahirle zühre meselesi \
 > T \
 > a \
 > ..... gider böyle \
 > 22 \
 > true \
 > 2 \
 > iseleseM erhüZ elrihaT \
 > Tahirle \
 > Zühre \
 > Meselesi \
  
  
  ## Ruby Diziler
  - Ruby dizileri, diğer dillerdeki diziler kadar katı değildir.Ruby dizileri String, Integer, Fixnum, Hash, Symbol gibi nesneleri ve hatta diğer Array nesnelerini tutabilir.
  - -1 indexi dizinin son elemanını gösterir, -2 ise sondan bir öncekinin , bu şekilde devam eder.
  - Dizi tanımı birden fazla şekilde yapılabilir.
  ```
  dizi = ["x","y",5]
  puts "#{dizi}"

  dizi2 = Array.new(20)
  puts dizi2.length # dizi2.size da aynı şeyi yapar

  dizi3 = Array.new(4,"bmt") # diziye 4 tane bmt değerini atar
  puts "#{dizi3}"

  dizi4 = Array.new(10){ |i| i = i*5 }
  puts "#{dizi4}"

  dizi5 = Array.[]("Aslında","hepsi","aynı")
  puts "#{dizi5}"

  dizi6 = Array["işi","yapıyor."]
  puts "#{dizi6}"

  dizi7 = Array(0..9)
  puts "#{dizi7}"
  ```
  Output:
  > ["x", "y", 5] \
  > 20 \
  > ["bmt", "bmt", "bmt", "bmt"] \
  > [0, 5, 10, 15, 20, 25, 30, 35, 40, 45] \
  > ["Aslında", "hepsi", "aynı"] \
  > ["işi", "yapıyor."] \
  > [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  
  - dizidedki elemanlara ulaşmak için ise
  ```
  dizi = ["x","y",5]
  puts "#{dizi.at(-1)}"
  ```
  Output: 
  > 5
  
  ## Ruby Aralıklar
  
 - Önceki konularda zaten örneklerini gördük.
 - (1..2), (87...95) , ('a'..'z')
 - ".." kullanıldığında son elemanı dahil ediyor.
 - "..." kullanıldığında son elemanı dahil etmiyor.
 - Kullanabileceğimiz bazı methodları var.
 ``` 
 rakamlar = 0...10

 puts rakamlar.include?(5) #içerip içermediğine göre true false döndürüyor.

 puts rakamlar.min # aralıkta en küçük değere sahip değişkenin döndürüyor.
 puts rakamlar.max # aralıkta en büyük değere sahip değişkenin döndürüyor.

 rakamlar = rakamlar.reject{ |i| i>=5} # verilen koşulu sağlayan değerler aralıktan çıkarılıyor.
 puts "#{rakamlar}" 

 rakamlar.each do |rakam| #foreach gibi aralıktaki tüm değerler için döngüye giriyor.
 puts "aralıktaki değer: #{rakam}"
 end
 ```
 Output:
 > true \
 > 0 \
 > 9 \
 > [0, 1, 2, 3, 4] \
 > aralıktaki değer: 0 \
 > aralıktaki değer: 1 \
 > aralıktaki değer: 2 \
 > aralıktaki değer: 3 \
 > aralıktaki değer: 4 \
 
 - 3 Çeşit kullanımı var.
   1- Dizi olarak aralıklar.
      - Aralıkları bir diziye atama yapabiliriz. Bunu için "to_a" ifadesi kullanmamız lazım.
      ```
      range=(1..10).to_a
      puts "#{range}"
      ```
      Output: 
      > [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
   
  
  2- Koşul olarak aralıklar.
     - when case konusunda örneği var.
  3- Ranges as Intervals \?
     - kapsama operatörü ile kullanılır. "==="
     ```
     istediğim_harfler = 'c'..'k'

     if  istediğim_harfler === 'd'
        puts "d içeriyor"
     elsif (istediğim_harfler === 'z')
        puts "z içeriyor."
     end
     ```
     Output:
     > d içeriyor
    
  
  
  
