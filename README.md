# Araştırma Ödevleri:

- [Araştırma Projesi 1 - Lateinit](#1)
- [Araştırma Projesi 2 - Tools Namespace](#2)
- [Araştırma Projesi 3 - Font Family XML](#3)
- [Araştırma Projesi 4 - Property Animation](#4)


### <a name="1"></a> Araştırma Projesi 1

- Lateinit neden kullanıyoruz?
- Lateinit kullanımından bahseder misiniz?
- Lateinit için bir örnek kullanım gösterir misiniz ?

### <a name="x"></a> Cevap:

Başlangıçta değer atamadan değişken tanımlamak için lazy ve lateinit kavramları kullanılır. Lateiniti  sadece var olan değişkenlerde kullanılırken, lazy sadece val olan değişkenlerde kullanılır.
Bir değişkene değer ataması bir sonraki aşamada gerçekleşmesi halinde lateinit işaretleyicisi kullanılır. Lateinit sadece non-nullable ve referans tipli değişkenlerde kullanılır. Bir değişkenin non-nullable olduğundan eminsek lateinit kullanabiliriz. Lateinit kullanmanın güzel bir yanı tanımlanan değişkeni kotlin non-null olarak görür ve sürekliolarak !! veya ? kullanmamıza gerek kalmaz.
Nullable değişken tanımlamak için ise 2 farklı yöntem vardır.
-	!! : Değişkeni tanıyoruz ve null olmadığına emin olduğumuz durumlar.
-	? : Değişkeni tam olarak tanımıyoruz. Null gelme ihtimali var. Eğer bu değişken null ise kod çalıştırılmadan geçilsin, uygulama çökmesin ama görsel hatalar olsun.

### <a name="x"></a> Lateinit Örnek Kullanım:
```
class MainActivity : AppCompatActivity() {
    private lateinit var button: Button   //Butona değer atamadan tanımladık
    private lateinit var textView: TextView  //TextView değer atamadan tanımladık
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
        button = findViewById(R.id.button)   //Buton değerini atadık
        textView = findViewById(R.id.textView)   //textView değerini atadık.
        
        button.setOnClickListener { 
            textView.text = "Text changed."
        }
        
    }
}
```

### <a name="2"></a> Araştırma Projesi 2


- Layout dizini içinde xml dosyalarımız için kullandığımız namespace nedir ?
- Neden kullanılmaktadır ?
- Nasıl kullanılmalıdır ?
- Bir adet Tools (tools namespace) attribute kullanımını gösterir misiniz ? 

### <a name="x"></a> Cevap:
Bir uygulama geliştirilirken tasarım tarafında yapılan değişiklerin çıktısını uygulamayı çalıştırmadan anında görebilmek için tools attribute(tools namespace) kullanırız.
Bu attribute birçok yerde kullanılabilir. Örneğin textView tasarlarken text değeri sabit bir değer olarak kalacaksa android:text=”text example” şeklinde bir kullanım yapabiliriz. Ancak değerimiz değişkense ve yine bu şekilde kullanırsak değer değişmeden önce kısa bir süre text example yazısını textview içerisinde görürüz. Bunun önünde geçmek için text değerini boş bırakabiliriz ya da tools:text=”text example” yazarak oraya gelecek bir textin nasıl görüneceğini sadece tasarım ekranımızda görebiliriz.

Bir zar uygulaması için örnek inceleyelim. Uygulamamızda bir buton ve zar olduğunu düşünelim. Uygulamamız ilk çalıştığında zarı ekranda görmeyeceğiz. Butona bastığımızda zar gelecek. Bu zarın nasıl görüneceğini uygulamayı çalıştırmadan tasarım ekranımzda görmek için tools attribute kullanabiliriz. Aşağıda kodumuzda kullanım örneği bulunmaktadır.
```
<ImageView
    android:id="@+id/imageView"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    app:layout_constraintBottom_toTopOf="@+id/mybutton"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.497"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintVertical_bias="0.54"
    android:src="@drawable/empty_dice"
    tools:src="@drawable/dice_1"
    />
```

`android:src=””@drawable/empty_dice”` ifadesi ile uygulamamızı çalıştırdığımızda empty_dice olur yani ekranda herhangi bir zar olmaz.
`tools:src=@drawable/dice_1”` ifadesi ile ekranda dice_1 yani zarın 1 olan görünümünü görebiliriz.
Yani tools attribute sayesinde yazılımcı tasarımını çalıştırmadan rahatlıkla görebilir.

![diceexample](https://github.com/beyzaaydemir/UpschoolBootcampResearchAssignments/blob/main/dice_image.png)


 
 Özetle, uygulamamız çalıştığında başlangıçta herhangi bir zar görüntüsü yoktur, butona bastığımızda ekrana zar gelecektir. Gelecek zarın nasıl görüneceğini yazılımcı projeyi çalıştırmadan tasarım ekranında öncesinde görebilir. Bunu da tools attribute sayesinde gerçekleştirir.

Bir diğer önemli attribute ise tools:listitem ’dır. Xml dosyamıza bir recyclerview eklediğimizde recyclerview içerisinde tasarımını yaptıktan sonra listemizdeki verilerin nasıl görüneceğini tools:listitem sayesinde görebiliriz. Mesela recyclerview içerisine json dosyasından okuduğumuz verileri bastırmak isityoruz. Uygulamayı çalıştırmadan önce verileri tasarım ekranında görebiliriz. Bu işlemi de Sample Data klasörü sayesinde tasarım ekranında gerçek verilerle çalışıyormuş gibi xml dosyalarımızı düzenleyebiliriz. Xml dosyasında tools attribute kullanarak gerçek verilerin nasıl göründüğünde uygulamamızı çalıştırmadan önce tasarım ekranında rahatlıkla görebiliriz.

### <a name="3"></a> Araştırma Projesi 3


- Font family dosyası nasıl oluşturulup kullanıyoruz? 
- Niçin böyle kullanımı tercih ediyoruz ?

Uygulamalarımızda tasarım konusunda dikkat edilmesi gereken konulardan birisi de tasarımımızın kullanıcı tarafında bırakacağı etkidir. Textview, buton ya da edittext gibi komponentleri kullanırken yapmış olduğumuz kullanıcı ara yüzüne uygun font kullanmalıyız.
XML Font Projelerimizde Nasıl Kullanılır? 
İlk olarak projemizde app seçeneğine sağ tıklıyoruz. New source file seçeneğini seçiyoruz. 
Dosyamıza isim veriyoruz ve resource type kısmını font olarak seçip OK butonuna basıyoruz.
Fontlarımızı oluşturacağımız XML dosyası res/font klasörü içerisine eklenmiş durumdadır. İstediğimiz bir fontu indirerek sıkıştırılmış dosya biçiminden çıkartıp oluşturmuş olduğumuz res/font/ içerisine .ttf uzantılı dosyayı atabiliriz. Font’un istediğimiz metinlerde nasıl görüneceğini görebilmek için üzerine iki kez tıklayıp görüntüleyebiliriz.
Oluşturduğumuz font.xml dosyamızı açılıyoruz ve bu dosyanın içerisine fontumuzu yazıyoruz.
```
<font-family 
   xmlns:android="http://schemas.android.com/apk/res/android">
   <font>
       android:fontStyle="normal"
       android:fontWeight="700"
       android:font="font/tapestry_regular"
   </font>
</font-family>
```
Tasarım ekranımızda bulunan textview içerisine fontumuzu ekliyoruz.
```
<TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="@font/tapestry_regular"
        android:text="Font Kullanım Örneği"
        android:textSize="34sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
```
Fontumuzu tasarım ekranında görüntülüyoruz.


![fontexample](https://github.com/beyzaaydemir/UpschoolBootcampResearchAssignments/blob/main/FontExample.png)

### <a name="4"></a> Araştırma Projesi 4

- Property Animation ile ilgili olarak objectAnimator ile animator arasındaki farkı kısaca açıklayınız. 

Arka plan rengi veya alfa değeri gibi bileşebib özelleiklerini belirli bir süre boyunca değiştiren animasyon türüdür. View ve view olmayan nesnelere uygulanabilir. View animasyondan en büyük farkı; view animasyonda view’in özellikleri değişmezken property animasyonda değişir.
Mesela view animasyonda siyah bir butonu animasyon ile maviye dönüştürürsek animasyon bitince siyah renge geri döner. Fakat property animasyonda geri eski rengine dönmez. Sadece renk için değil boyut konum için de aynı durum geçerlidir. Değiştirilen değer artık o bileşenin kendi özelliği olur.
3 farklı property animasyon sınıfı vardır:
1)	Value Animator: Bu sınıf, animasyonlu değerleri hesaplayan ve bunları hedef nesnelere ayarlayan animasyonları çalıştırmak için basit bir zamanlama motoru sağlar.
2)	Object Animator: Tek bir nesneye animasyon vermek istediğimiz zaman kullanılır. Object animator sınıfı value animatör sınıfının alt sınıfıdır.
3)	Animator Set: Animasyonların belirlenen sırada uygulanmasını sağlar.

```
Object Animator Kullanımı:
<objectAnimator 
        android:propertyName="string"       <!--İlgili animasyonun adı-->
        android:duration="int"               <!--animasyon süresi-->
        android:valueFrom="float | int | color"  <!--Yapılacak animasyon-->
        android:valueTo="float | int | color"     <!--Yapılacak animasyon-->
        android:startOffset="int"             <!--Gecikme süresi-->
        android:repeatCount="int"             <!--Tekrar sayıyı-->
        android:repeatMode=["restart" | "reverse"]  <!--Tekrar edilme şekli-->
        android:valueType=["intType" | "floatType"]/>
```
```
Animator Kullanımı:
<animator
        android:duration="int"               <!--animasyon süresi-->
        android:valueFrom="float | int | color"   <!--Yapılacak animasyon-->
        android:valueTo="float | int | color"     <!--Yapılacak animasyon-->
        android:startOffset="int"                 <!--Gecikme süresi-->
        android:repeatCount="int"                 <!--Tekrar sayıyı-->
        android:repeatMode=["restart" | "reverse"] <!--Tekrar edilme şekli-->
        android:valueType=["intType" | "floatType"]/>

```





