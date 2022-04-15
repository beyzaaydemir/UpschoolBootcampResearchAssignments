# Araştırma Ödevleri:

- [Araştırma Projesi 1 - Lateinit](#1)
- [Araştırma Projesi 2 - Tools Namespace](#2)


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


 
 Özetle, uygulamamız çalıştığında başlangıçta herhangi bir zar görüntüsü yoktur, butona bastığımızda ekrana zar gelecektir. Gelecek zarın nasıl görüneceğini yazılımcı projeyi çalıştırmadan tasarım ekranında öncesinde görebilir. Bunu da tools attribute sayesinde gerçekleştirir.

Bir diğer önemli attribute ise tools:listitem ’dır. Xml dosyamıza bir recyclerview eklediğimizde recyclerview içerisinde tasarımını yaptıktan sonra listemizdeki verilerin nasıl görüneceğini tools:listitem sayesinde görebiliriz. Mesela recyclerview içerisine json dosyasından okuduğumuz verileri bastırmak isityoruz. Uygulamayı çalıştırmadan önce verileri tasarım ekranında görebiliriz. Bu işlemi de Sample Data klasörü sayesinde tasarım ekranında gerçek verilerle çalışıyormuş gibi xml dosyalarımızı düzenleyebiliriz. Xml dosyasında tools attribute kullanarak gerçek verilerin nasıl göründüğünde uygulamamızı çalıştırmadan önce tasarım ekranında rahatlıkla görebiliriz.




