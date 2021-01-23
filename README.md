# Android Geliştiricilerin Bilmesi(en azından fikir sahibi olması) Gereken Core Bilgiler

#### Prepared by [developersancho](https://github.com/developersancho) who is having experience and work on Android Development.

## Sorular
* **[Class-Object Nedir?](#class-object-nedir)**
* **[Memory Leak Nedir?](#memory-leak-nedir)**
* **[Big O Notasyonu Nedir?](#big-o-notasyonu-nedir)**
* **[Queue ile Stack arasındaki fark nedir?](#queue-ile-stack-arasndaki-fark-nedir)**
* **[MultiThread Nedir?](#multithread-nedir)**
* **[THREADS](#threads)**
* **[Paralel Programlama nedir?](#paralel)**
* **[Asenkron Programlama(Concurrency) nedir?](#asenkron)**
* **[COROUTINE nedir? ](#coroutine)**
* **[OOP(Object Oriented Programming)](#oop)**
* **[Yazılım Geliştirme Modelleri](#ygm)**
* **[Android 11](#android-11)**
* **[Android 10](#android-10)**
* **[KOTLIN](#kotlin)**
* **[Inline Functions & Reified types](#inline-reified)**
* **[SOLID Prensipleri Nedir?](#solid)**
* **[ADB(Android Debug Bridge) nedir?](#adb)**
* **[NDK nedir?](#ndk)**
* **[Bitmap nedir?](#bitmap)**
* **[Vektörel Grafik nedir?](#vector)**
* **[Multidex nedir?](#multidex)**
* **[FileProvider Nedir?](#fileprovider)**
* **[ListView ile RecyclerView arasındaki farklar nelerdir?](#recyclerview)**
* **[Constraint Layout Özellikleri](#constraint)**
* **[Screen rotation edildiğinde activity lifecycle nasıl çalışır?](#rotation)**
* **[Serializable ve Parcelable nedir? Farkları nelerdir? ](#parcelable)**
* **[Bundle ile en fazla kaç mb veri taşınır?](#bundle)**
* **[Build Type ve Product Flavor arasındaki fark nedir?](#build)**
* **[ProGuard Nedir?](#proguard)**
* **[Context Nedir?](#context)**
* **[Service nedir?](#service)**
* **[Broadcast Receiver nedir?](#broadcast-receiver)**
* **[Activity ve Fragment Nedir?](#activity-fragment)**
* **[Activity ve Fragment Arasındaki Farklar Nelerdir?](#activity-fragment-farklar)**
* **[Activity Fragment Lifecycle Nedir?](#lifecycle)**
* **[Activity Lifecycle Metodları?](#lifecycle-methods)**
* **[SharedPreferences'e veri kaydetme metotlarından commit() ve apply() arasındaki farklar nedir?](#pref-apply-commit)**
* **[Veri Saklama Yöntemleri Nelerdir?](#veri-saklama)**
* **[Content Provider Nedir?](#content-provider-nedir)**
* **[Launch Mode çeşitleri nelerdir?](#launch-mode)**
* **[Application Class Nedir?](#application-class)**
* **[Gradle Nedir?](#gradle)**
* **[Android Manifest.xml Nedir?](#android-manifestxml-nedir)**
* **[Intent Nedir?](#intent)**

#### <a name="class-object-nedir"></a> Class-Object Nedir?
    * Class nesnelerin durumunun tanımlandığı yerdir.
    * Object Class'ın somut hale getirilmesidir. Class'ın davranış kazanmasıdır. 

#### <a name="memory-leak-nedir"></a> Memory Leak Nedir?
    * Belleğin(RAM) taşması demektir. Kullanılmayan nesnelerin bellekte tutulmasıdır.
    * Nesne oluşturulduğunda bellekte "(HEAP)" saklanır, sonrasında saklınılan yerden 
    bu işaretlenen nesnenin(kullanılmayan) silinememesi durumunda memory leak oluşur.
    * Garbage Collection'ın leak oluşturan nesneleri bellekten silememesi durumudur.
 
* Bellekte nesneler ve değer tipleri tutulur ve bunlar `STACK` ve `HEAP`' te saklanır.

###### Stack
    * Bellek içerisinde değer tipleri ve nesne referansları tutulur.
    * İlk giren son çıkar.
    * Bellekte son kısma gelindiğinde temizlenir.
    * Bir nesne oluşturulduğunda nesne heap üzerinde, referansı stack'te tutulur.
    * Stack'te taşma durumu olursa "StackOverFlow" hatası fırlatılır.
###### Heap
    * Kendisi dinamiktir. Stack' e göre yavaştır.
    * Nesne oluşturulduğunda Heap' te tutulur.
    * Bellek JVM tabanında referansı bulunan nesneleri işaretler, geriye kalanları temizler.
    * Heap'te taşma durumu olursa "OutOfMemory" hatası fırlatılır.
###### Garbage Collection
    * Aktif olan nesnelerin bellekteki referanslarını tespit eder ve işaretler.
    * İşaretlenmemiş tüm nesneleri bellekten temizler.
    * Aktif olan nesneleri yeniden düzenler.
    * Garbage Collection devreye girdiğinde UI(Kullanıcı Arayüzü) bir miktar(16ms) gecikir fakat 
    kullanıcı bunu farkedemez bu gecikme süresi(işlem süresi) 100ms+ olursa UI cevap vermemeye başlar. 
    Bu cevap vermeme süresi 5 sn' den uzun sürerse ANR - (A)pplication (N)ot (R)esponding 
    uyarı penceresi çıkar.
###### ANR (A)pplication (N)ot (R)esponding
    * ANR, "(A)pplication (N)ot (R)esponding" anlamına gelir. UI thread'de uzun süren 
    (5 saniye içerisinde yanıt alınamayan) işlemlerde Android işletim sistemi tarafından 
    gösterilen bir dialogdur.
###### Dikkat edilmesi gereken noktalar
    * Bir listener ve ya receiver register edildikten sonra bulunduğu lifecyle destroy edilmeden önce 
    unregister yapılmalıdır.
    * İçe içe sınıf referansları tanımlanırken "inline" keywordu kullanılmalıdır.
    * Activity ve ya View referansları static tanımlanacağı zaman WeakReference olarak tanımlanmalıdır.
```kotlin
private var activity: WeakReference<Activity>? = null
```

#### <a name="big-o-notasyonu-nedir"></a> Big O Notasyonu Nedir?
    * Bir algoritmanın performansını ve ya Time Complexity'sini hesaplamak için kullanılır.
###### Time Complexity
    * Bir algoritmanın çalışması için gerekli olan süredir. Bu süre işlem sayısına göre hesaplanır.
    
    
#### <a name="queue-ile-stack-arasndaki-fark-nedir"></a> Queue ile Stack arasındaki fark nedir?
    * Queue → FIFO(İlk giren ilk çıkar), Stack → LIFO(Son giren ilk çıkar)
    
    
#### <a name="multithread-nedir"></a> MultiThread Nedir?
    * Bir uygulamanın aynı anda birden fazla iş parçacıklarını(threads) işlemesidir.
###### Synchronization — Eş zamanlama
    * İlgili kod parçacığına aynı anda sadece bir iş parçacığı erişir ve diğerleri onu bekler.
    
#### <a name="threads"></a> THREADS
1) UI(Main) Thread
2) Background(Worker) Thread
3) Binder Thread 

##### UI(Main) Thread
    * Android UI güncellenmesi bu thread üzerinde gerçekleşir.
##### Background(Worker) Thread
    * Uzun sürecek işlemleri UI Thread'i meşgul etmeden arka planda yapılmasını sağlar.
    * Örnek olarak webservice istekleri, firebase database işlemleri verilebilir.
##### Binder Thread
    * Farklı işlemler içindeki thread'leri birbirleriyle haberleşmesi için kullanılır.
    * Tüm sistem servisleri(Intent, Content Provider, Telephone, Vibrator, Wifi, Battery, Notification vb.)
    binder thread-> IPC(Inter Process Communication) üzerinden faydalanır.
    Örn: Content Provider ile Contacts bilgilerinin alınması, Activity Lifecyle metotlarının ActivityManagerService
    tarafından çağrılması
    
#### <a name="paralel"></a> Paralel Programlama nedir?
    * Bir görevi paralel olarak işlenebilecek daha küçük alt görevlere ayrılacak birden fazla CPU'da 
    thread'ler ile yürütülmesi sağlanır.
    
#### <a name="asenkron"></a> Asenkron Programlama(Concurrency) nedir?
    * Bir uygulamanın aynı anda birden fazla görevi, işi yapmasıdır. Ama bu işler paralel olarak farklı 
    thread'lerde işlenmeyebilir.
    * Uzun süren IO işlerinin CPU'yu bloklamaması amacıyla kullanılır.
    * Kotlin bu yöntemi sağlamak için COROUTINE denilen bir yapı sunar.
    
    
#### <a name="coroutine"></a> COROUTINE nedir?    
    * Thread değildir. LightWeight thread denilir.
    * Thread tarafından yürütülen iş parçalarıdır.    
##### suspend nedir?
    * Mevcut thread'ı bloke etmeden coroutine yürütülmesini askıya alır, sıralı işletilir.
##### async nedir?
    * Geriye değer dönen asenkron işlemler için kullanılır.
##### launch nedir?
    * Geriye değer dönmeyen işlemler için kullanılır. Çalıştır-Unut prensibiyle çalışır.
##### runblocking nedir?
    * İlgili coroutine tamamlana kadar mevcut thread' bloke eder.

#### <a name="oop"></a> OOP(Object Oriented Programming)
    * OOP denildiğinde aklımıza aşağıdaki 4 kavram gelmelidir.
    → Abstraction(Soyutlama)
    → Inheritance(Kalıtım)
    → Encapsulation(Kapsülleme) 
    → Polymorphism(Çok Biçimlilik)
    
###### Abstraction(Soyutlama)
    * Nesneye yalnızca ilgili ayrıntıları göstermek için daha büyük bir havuzdan veri seçme işlemidir.
    * Interface ve abstract class' lar ile yapılır.    
###### Inheritance(Kalıtım)
    * Kendisine ait olan özelliklerin, işlevlerin başka bir sınıfa aktarılması olayıdır.
###### Encapsulation(Kapsülleme)
    * class içerisindeki değişkenlerin get ve set metotlarının oluşturulması
    → private: sınıfa özel değişkenler
    → public: herkese açık değişkenler
    → protected: türetilen sınıfa ve aynı pakette olanlara açık değişkenler
    → static: sınıf değişkeni, instance oluşturulmadan kullanılır
    → final: sadece bir değer ataması yapılır
    → constant: compile time'da son değer set edilir Örn: DateTime
###### Polymorphism(Çok Biçimlilik)
    * Bir nesnenin farklı bir nesne gibi davranmasıdır
###### Abstract Class ile Interface arasındaki farklar.    
    * abstract class tekli kalıtım, interface çoklu kalıtım destekler.
    * abstract class yapıcı metot içerebilir, interface yapıcı metot içermez.
    * abstract class static üyeler içerebilir, interface static üyeler içermez.
    * abstract class farklı tipte(private, public,..) değişken içerir, interface sadece public değişken tanımlanır.
    * abstract class is-a ilişkisi vardır, interface can-do ilişkisi vardır.
    * en az bir abstract metot varsa class abstract olmalı, interface içi boş olabilir.
    * abstract metotların gövdesi yoktur, interface metotların gövdesi olabilir.
###### super()
    * Bir alt sınıfın bir üst sınıfa erişmesini sağlar.    

#### <a name="ygm"></a> Yazılım Geliştirme Modelleri
    * Bir yazılımın, üretim aşaması ve kullanım süreci boyunca geçirdiği tüm aşamalar yazılımın yaşam döngüsüdür.
##### WaterFall(Şelale)
    * Planlama-Analiz-Tasarım-Geliştirme-Test-Uygulama, buradaki aşamaları sırayla gerçekleştirilir.
    * Bir aşama bitmeden diğer aşamaya geçilmez.
    * İletişim tek yönlüdür.
    * Bir önceki aşamaya geri dönüş çok zordur.
##### Agile(Çevik)
    * WaterFall'daki problemleri çözmek üzere çıkmış tekrarlanan yazılım geliştirme modelini taban alarak 
    sık aralıklarla parça parça teslimatın yapıldığı modeldir.
    * İş parçalara bölünür, süreç böyle işlenir.
    * Ekipte En fazla 9, en az 3 kişi bulunur.
###### Agile(Çevik)-Kullanılan Metodolojiler
    * Scrum
    * Kanban
    * XP(Extreme Programming)
    * TDD(Test Driven Development)
    * FDD(Feature Driven Development)

#### <a name="android-11"></a> Android 11
    * Wireless Debuging
    * Bubbles
    * IME Animations
    * Privacy
    * AutoFill
    * Background Location
    * 5G Support
    * Foldo

#### <a name="android-10"></a> Android 10
    * Dark Theme
    * 5G Support
    * Gesture Navigation
    * ShorcutInfo API
    * Location Controls
    
    
    
#### <a name="kotlin"></a> KOTLIN
    * NullCheck
    * val,var
    * when
    * high order function(let, run, apply, with)
    * extension function
    * type alias
    * DSL infix notation(dsl üretme, infix fun Int.plus(c: Int) -> 15.plus(5) yerine 15 plus 5 yazılır.)
    * delegation (değişkenlerin değerinin yönetimini başka bir fonksiyona veriyoruz.)
    
    
#### <a name="inline-reified"></a> Inline Functions & Reified types
    * Arka planda fonksiyon her çağrıldığında aldığı parametre için bir nesne oluşturur. Doğru yerde 
    kullanılmadığında belleğe yük olur.
    * Fonksiyona inline dediğimizde parametre için nesne oluşturmaz, çağrıldığı yerde çalışması için
    bir kod bloğu görevi üstlenir.
    * reified dediğimizde parametre alma zorunluluğu kaldırılır.
* ilk hali
```kotlin
fun <T: Any> Retrofit.create(service: KClass<T>): T = create(service.javaObjectType) 
```        
* son hali
```kotlin
inline fun <reified : T> Retrofit.create(): T = create(T::class.java)
```     
    
#### <a name="solid"></a> SOLID Prensipleri Nedir?
    * SOLID yazılım prensipleri; geliştirilen yazılımın esnek, yeniden kullanılabilir, sürdürülebilir 
    ve anlaşılır olmasını sağlayan, kod tekrarını önleyen ve Robert C. Martin tarafından öne sürülen 
    prensipler bütünüdür.
###### S — Single-responsibility principle
    * Bir sınıf (nesne) sadece bir işten sorumludur.
###### O — Open-closed principle
    * Bir sınıf (nesne) gelişime açık, değişime kapalı olması.
###### L — Liskov substitution principle
    * Alt sınıfları, türedikleri(üst) sınıfların yerine kullanma.
###### I — Interface segregation principle
    * Sorumlulukların hepsini tek bir arayüze toplamak yerine daha özelleştirilmiş birden fazla arayüz oluşturma
###### D — Dependency Inversion Principle
    * Bağımlılığı tersine çevirme, daha az bağımlı olma.

#### <a name="adb"></a> ADB(Android Debug Bridge) nedir?
    * Android bir cihaz ile iletişim kurulmasını sağlayan bir yapıdır.

#### <a name="ndk"></a> NDK nedir?
    * Android uygulamalarımızda C ve ya C++ dillerinde geliştirilmiş olan kodlarımızı
    kullanmamızı sağlayan bir araçtır.
    
    
#### <a name="bitmap"></a> Bitmap nedir?
    * PNG, JPEG, BMP, GIF gibi dosya formatları bitmap olarak isimlendirilir. Resim için 
    renkler ve konumları bir harita gibi işler.
    
    
#### <a name="vector"></a> Vektörel Grafik nedir?
    * Path halide tutulur.
    * Bir çizgi başlangıç ve bitiş noktasının bilgisi tutulur. Dosya çalıştırılınca parse edilir,
    bitmap'e dönüştürülür.
    
    
#### <a name="multidex"></a> Multidex nedir?
    * APK dosyalarında .dex(Dalvik Executable) uzantısına sahip dosyalar bulunur. 
    * Bir dex dosyası 65,536'den referansa(metot) sınırlar. 
    * Bu sınır geçiliyorsa multidex enable true yapılmalıdır(21+).
    * Aksi halde “Error: Cannot fit requested classes in a single dex file.Try supplying a main-dex list. # methods: 72477 > 65536”
    hatası alır.

#### <a name="fileprovider"></a> FileProvider Nedir?
    * 19+ için izin almadan kamera ile fotoğraf çekip app external storage kaydetmesini sağlar.

#### <a name="recylerview"></a> ListView ile RecyclerView arasındaki farklar nelerdir?
    * Listview bütün datayı ekran açılırken yükler, RecylerView ekranı kaydırdıkça yükler.
    * Listview'de yatay(horizontal) kaydırma yoktur, Recylerview'de yatay kaydırma vardır.
    * Listview'de onItemClick vardır, Recylerview'de yoktur.
    
    
#### <a name="constraint"></a> Constraint Layout Özellikleri
    * Response tasarımlar için idealdir. Performanslıdır
    * Weight dinamik olarak ayarlanabilir.
    * Chain oluşturularak view'ler gruplandırılabilir.
    * Farklı ekran boyutları için daha kullanışlıdır.
    * Düz görünüm hiyerarşisine sahiptir.
###### Tercih Eilmesinin En Önemli Sebebi
    * Diğer layoutlar(Relative, Linear) içerisindeki view'ları iç içe döngü içerisinde çizilir(Nested Loops).
    * Consraint layout düz görünüm hiyerarşine sahip olduğu için(tree structure) döngü içerisinde çizilmez. 
    Bundan dolayı diğerlerine göre çok performanslıdır.

#### <a name="rotation"></a> Screen rotation edildiğinde activity lifecycle nasıl çalışır?
    * Uygulama start edilir
    * Sırası ile onCreate() -> onStart() -> onResume() -> Cihaz rotation yapılır 
    -> onPause() -> onStop() -> onSaveInstanceState() -> onDestroy() 
    -> onCreate() -> onStart() -> onRestoreInstanceState(), onResume() metotları çalışır.

#### <a name="parcelable"></a> Serializable ve Parcelable nedir? Farkları nelerdir? 
    * Parcelable, Serializable göre daha hızlı, performanslıdır.
    * Parcelable android için geliştirilmiştir.
    * Serializable java interface'idir.
    
    
#### <a name="bundle"></a> Bundle ile en fazla kaç mb veri taşınır?
    * En fazla 1 MB veri taşınır. Fazlası için memory cache ve ya local cache kullanabilir.

#### <a name="build"></a> Build Type ve Product Flavor arasındaki fark nedir?
    * Build Type, uygulamanın paketlenmesi
    * Product Flavor, uygulama için kullanıcıya yayınlayabileceğimiz farklı sürümler oluşturmamızı sağlar.

#### <a name="proguard"></a> ProGuard Nedir?
    * Geliştirilen uygulamaların kaynak kodlarını karıştırmaya ve sıkıştırmaya 
    (uygulama boyutunu düşürmeye) yarayan ücretsiz 3. parti bir kütüphanedir.

#### <a name="context"></a> Context Nedir?
    * Context, uygulamanın herhangi bir zamandaki durumunu tutan bir objedir.
    * Uygulamadaki kaynaklara referans olarak her yerden erişmemizi saglayan Android işletim sistemi 
    tarafından implement edilmiş bir Interface'dir. 
    * Uygulamanın /res klasöründe bulunan kaynaklara (stringler, resim dosyaları vs.) erişimi 
    sağlamak için kullanılır. 
    * Yeni bir Activity başlatma, Intent'leri kullanma gibi işler de Context tarafından yapılır.
    * 4 tanedir. Bunlar; Activity, Service, Broadcast Receiver, Content Provider

* `Application Context`, getApplicationContext() metoduyla uygulamanın herhangi bir yerinden uygulama Context’ini alır, 
singleton’dır,uygulamayla aynı yaşam süresine sahiptir.
* `Activity Context`, ActivityName.this yoluyla çağrılır ve Activity ile aynı yaşam süresine sahiptir. 
Daha çok o Activity içerisindeki objelerde kullanılır. Service’ler de aynı mantıktadır. Activity’nin kendisi Context’i implement eder.
* `ContentProvider`, herhangi bir Context barındırmaz, sahip olunan getContext() metodu ile uygulama Context’i alınabilir.
* `BroadcastReceiver`, kendisi herhangi bir Context barındırmaz. onReceive() metoduyla Context alabilir.

#### <a name="service"></a> Service nedir?
    * Arayüzü olmayan arka planda çalışan yapıdır.
    * 2 tanedir.
###### Foreground Service
    * UI thread'de çalışır. Service'ten extend edilir. 
###### Background Service
    * Background thread'de çalışır. IntentService'ten extend edilir. 

#### <a name="broadcast-receiver"></a> Broadcast Receiver nedir?
    * İşletim sistemi genelinde bir uygulama ve ya kendisinin bir parçası tarafından yayınlanan
    sinyallerin dinlenmesini sağlar.

#### <a name="activity-fragment"></a> Activity ve Fragment Nedir?
    * Activity’ler, Android platformundaki uygulamaların temel yapı taşlarından biridir.
    * Etkileşimli bir uygulama için bir giriş noktası işlevi görürler ve kullanıcıya bir uygulama aracılığıyla erişebilirler.
    * Fragment, bir Activity’de activity veya kullanıcı arabiriminin bir bölümünü temsil eder. Çoklu UI oluşturmak amacıyla kulanılır.

#### <a name="activity-fragment-farklar"></a> Activity ve Fragment Arasındaki Farklar Nelerdir?
    * Activity tek başına oluşturulabilir. Fragment oluşturmak için Activity'e ihtiyaç vardır.
    * Activity birden fazla fragment içerebilir.
    * Her ikisininde kendine ait yaşam döngüleri vardır.(Lifecycle)

#### <a name="lifecycle"></a> Activity Fragment Lifecycle Nedir?
    * Bir kullanıcı, uygulamanızda gezinirken, uygulamanın dışındayken ve geri döndüğünde, uygulamanızdaki Activity'ler 
    yaşam döngüsünde farklı hallerde geçiş yapar.
     * Activity sınıfı, bir durumun değiştiğini activity’ye bildirebilmesini sağlayan bir dizi geri arama sağlar:
    sistem, bir activity oluşturuyor, durduruyor, devam ettiriyor veya etkinliğin bulunduğu işlemi yok ediyor.
    * Yaşam döngüsü geri arama yöntemleri içinde, kullanıcı uygulamayı terk edip yeniden girdiğinde etkinliğinizin nasıl davrandığını bildirebilirsiniz.

#### <a name="lifecycle-methods"></a> Activity Lifecycle Metodları?
* `onCreate()` Activity başlatıldığında ilk çağırılan metoddur.
* `onStart()` onCreate metodu çalıştırıldıktan sonra, görsel ögeler (tasarım) oluştuğunda çağırılan metoddur.
* `onResume()` Eğer activity durdurulduysa, onResume ile tekrar aktif hale getirilir.
* `onPause()` Activity arka plana atıldığında çalışır (cihazın back tuşuna basılması vs.)
* `onStop()` onPause gibi activity arka plana atıldığında çalışır. onStop için iki durumdan bahsedebiliriz. 
Bunlar kullanıcının veya uygulamanın tekrar aynı activitye dönmesi veya bir daha activitye geri gelmemesidir. 
Activitye geri dönüldüğü taktirde onRestart -> onStart metodları çalışır, ikinci durumda ise onDestroy metodu ile yaşam döngüsü tamamlanır.
* `onDestroy()` Yaşam döngüsünü tamamlanır. Bir activitye ait bütün kaynaklar temizlenir.

* `onRestart()`
 Kullanıcıya uygulamaya geri döndüğünde onStop () ‘dan sonra çağrılır. OnStart () ve onResume () takip eder

* `onSaveInstanceState()`
Öldürülmeden önce bir etkinlikten örnek durumunu almak için çağrılır ve böylece durumun onCreate (Bundle) veya 
onRestoreInstanceState (Bundle) (bu yöntemle doldurulan Bundle her ikisine de geçilir) olarak geri yüklenebilir.
Bu yöntem, bir etkinliğin öldürülmesi öncesinde çağrılır; böylece gelecekte bir süre geri döndüğünde duruma geri yüklenebilir.

* `onRestoreInstanceState()`
Bu yöntem, onStart () işleminden sonra, burada savedInstanceState içinde verilen önceden kaydedilmiş bir durumdan yeniden başlatıldığında kullanılır.
Çoğu uygulama, yalnızca durumunu düzeltmek için onCreate kullanır, ancak bazen başlatma tamamlandıktan sonra varsayılan uygulamanızın 
kullanılıp kullanılmayacağına izin vermek için bunu yapmak daha uygun olacaktır.
Bu yöntemin varsayılan uygulaması, daha önce onSaveInstanceState (Bundle) tarafından dondurulmuş olan herhangi bir görünüm durumunun 
geri yüklenmesini gerçekleştirir.
Bu yöntem, onStart () ve onPostCreate (Paket) arasında çağrılır.

* `onActivityResult()`
Uygulama açıldığında, size gönderilen requestCode kodunu döndürdüğü resultCode’u ve ona ait ek verileri veren metot’dur.
Uygulama açıkça döndürürse, sonuç döndürmezse veya işlem sırasında çöktüğünde resultCode RESULT_CANCELED olur.
Bu çağrıyı, etkinliğiniz yeniden başladığında onResume () ‘dan hemen önce alacaksınız.
Bu yöntem, activity içerisinde noHistory değerini true olarak ayarlanırsa hiçbir zaman çağrılmaz.

* `onBackPressed()`
Activity içerisinde geri geldiğimizde tetiklenen metottur.

#### <a name="pref-apply-commit"></a> SharedPreferences'e veri kaydetme metotlarından commit() ve apply() arasındaki farklar nedir?
    commit() senkron gerçekleşir, apply() asenkron gerçekleşir.
    senkron işlemlerde geri dönüş değeri beklenir, asenkron işlemlerde çalış unut prensibi yatar.
    commit 'te işlem başarılı ise true, başarısız ise false döner. apply arka planda gerçekleşir değer dönmez.
    apply commit'e göre daha hızlıdır.

* Use apply(). It writes the changes to the RAM immediately and waits and writes it to the internal storage(the actual preference file) after. 
Commit writes the changes synchronously and directly to the file.

#### <a name="veri-saklama"></a> Veri Saklama Yöntemleri Nelerdir?
    1- SharedPreferences
    2- DB(ROOM)
    3- Content Provider(İçerik Sağlayıcı)
    4- Internal Storage
    5- External Storage
    6- Local Cache
    7- Remote Connection(Firebase, Webservice)

#### <a name="content-provider-nedir"></a> Content Provider Nedir?
    * Bir uygulamanın, diğer uygulamalar tarafından depolanan verilere erişimi yönetmesini ve 
    diğer uygulamalara veri paylaşımını sağlayan bir yapıdır.
    * İçerik sağlayıcılar, bir işlemdeki verileri başka bir işlemde çalışan kodla bağlayan 
    standart arabirimdir.

#### <a name="launch-mode"></a> Launch Mode çeşitleri nelerdir?
    Bir uygulamada oluşturulan activity instance'larının tekrardan kullanıp kullanılamacağını belirleyen kurallardır.
* `standart:` Her bir Intent çağrısı için yeni bir tane Activity oluşturulur.
* `singleTop:` Intent çağrısı zaten oluşturulmuş bir Activity için çağırılırsa yeni bir Activity oluşturulmaz, onun yerine var olan 
Activity instance kullanılmaya devam edilir. Bu mod kullanımında onNewIntent ve onCreate metotlarında düzenlenmelidir.
* `singleTask:` Çağrılan bir Activity' den sadece tek bir instance oluşturabilir. Sistem içerisinde zaten var olan bir Activity' e 
istek gönderilirse onNewIntent metodu kontrol edilmelidir.
* `singleInstance:` singleTask moduna benzer. Ancak bu activity' i tutan task sadece tek bir singleInstance olarak tanımlanmış 
activity' i barındırabilir.

#### <a name="application-class"></a> Application Class Nedir?
    * Application Class, Activity ve Services gibi bileşenleri içeren Android uygulamasının temel sınıfıdır.
    * Uygulama veya alt sınıfları, Android uygulamasında tüm etkinlikler veya diğer uygulama nesneleri oluşturulmadan önce başlatılır.

#### <a name="gradle"></a> Gradle Nedir?
    * Android uygulaması geliştirme aşamalarını otomatize eden açık kaynak kodlu Android Studio üzerinde çalışan bir yapı sistemidir.
    * Bir Android projesinin oluşturulmasından tamamlanmasına giden yolda derleme, test etme, paketleme gibi işlemler söz konusudur.
    * Gradle, Android uygulaması geliştirme aşamalarını yapılandırmamızı sağlayan, açık kaynak kodlu, Android Studio üzerinde çalışan 
    bir inşa sistemidir.
    * Android Studio üzerinde bir proje oluşturduğumuzda, Gradle build sistemi otomatik olarak devreye girer ve build işlemini gerçekleştirir.
    Burada build etmekten anlayacağımız; uygulama kaynaklarını ve kaynak kodunu derlemek, bunları test edilebilir-uygulanabilir-imzalanabilir 
    ve yayınlayacağımız APK’lar haline getirmek olmalıdır.

* `buildscript:` Gradle’ın kendi depolarını ve bağımlılıklarını yapılandırdığımız bloktur.
* `repositories:` Gradle’ın depolarını veya kendi uzak depolarımızı tanımladığımız yerdir.
* `dependencies:` Projeyi oluşturmak için Gradle’ın kullanması gereken bağımlılıkların eklendiği yerdir.
* `allprojects:` Bu blok özel özellikleri taşır ve bunları tüm proje üzerindeki modüllere sunar.
* `apply plugin:` Android üzerinde kullanılan eklentilerin Android üzerinde kullanılabilir hale getirilmesi için belirtildiği satırdır.
Örneğin görselde kotlin-android eklentisini belirtmişiz.Projemiz kotlin koduyla yazılıp derlenebilecek.
* `applicationId:` Uygulamamızın paket adıdır.
* `minSdkVersion:` Uygulamanın en düşük hangi sürümde çalışabileceğini belirtir.
* `targetSdkVersion:` Uygulama için belirlenen geçerli versiondur.SDK platformunun en yüksek version değerini almalıdır.
Eğer bu değer belirtilmediyse minSdkVersion değeri ne ise o kullanılır.Her yeni Android sürümü çıktığında targetSdkVersion güncellenmelidir 
ki uygulamamızda yer alan bazı özelliklerin son sürümle uyumlu çalışıp çalışmadığını görelim.
* `compileSdkVersion:` Uygulamayı compile etmek istediğimiz versiondur.minSdkVersiondan düşük olmamalıdır.
* `buildToolsVersion:` Dependencies bloğundaki kütüphanelerin uygulamamızla uyumlu kullanabilmemiz için, kütüphanelerin versionlarının 
buildToolsVersion versionuna eşit olması gerekir
* `versionCode:` Uygulamamızı Play Store’a yüklerken ve güncelleyeceğimiz zaman sayısal olarak tutulan version değeridir.
* `versionName:` Version bilgisinin metinsel halidir.

#### <a name="android-manifestxml-nedir"></a> Android Manifest.xml Nedir?
    * Uygulamamızın adını, iconunu, temasını bildirir.
    * Uygulamada kullanılacak version numaralarını, kütüphaneleri, minimum ve geçerli SDK sürümlerini bildirir.
    * Uygulamanın gerektirdiği veya uygulamada kullanacağımız yazılım-donanım özelliklerini bildirir. (kamera, bluetooth vs.)
    * Uygulama izinleri belirlerlenir. (internet bağlantısı, kullanıcı izinleri vs.)
    * Activitylerimizi yönetir ve bu activitylerin özelliklerini bildirir.(Tema, Orientation Mode,...)

#### <a name="intent"></a> Intent Nedir?
    * Activity'ler arası veri taşımak için kullanılır.(Bundle)
    * Activity, service, Broadcast Receiver, ContentProvider, diğer uygulamalar arasında haberleşmeyi sağlar.
    * 2' ye ayrılır.

* `Explicit(açık) Intent` → aktiviteler arası geçiş. (Bundle, Intent)
* `Implicit(üstü kapalı) Intent` ( Telefon araması yapmak, mesaj(sms), mail göndermek, foto ve video çekmek)

## ##

![TEAMS](4366818.jpeg "teams")

## KATKI SAĞLAYANLAR ##
* [developersancho](https://github.com/developersancho)
* [mucahitkambur](https://github.com/mucahitkambur)

