# Android Geliştiricilerin Bilmesi(en azından fikir sahibi olması) Gereken Core Bilgiler

#### Prepared by [developersancho](https://github.com/developersancho) who is having experience and work on Android Development.

## İçerik
* <a href="#anr-nedir">ANR Nedir?</a>
* <a href="#context-nedir">Context Nedir?</a>

## Sorular

#### ANR Nedir?
    ANR, "(A)pplication (N)ot (R)esponding" anlamına gelir. UI thread'de uzun süren (5 saniye içerisinde yanıt alınamayan)
    işlemlerde Android işletim sistemi tarafından gösterilen bir dialogdur.

#### Context Nedir?
    Context, uygulamanın herhangi bir zamandaki durumunu tutan bir objedir.
    Uygulamadaki kaynaklara referans olarak her yerden erişmemizi saglayan Android işletim sistemi tarafından implement edilmiş bir Interface'dir.
    Uygulamanın /res klasöründe bulunan kaynaklara (stringler, resim dosyaları vs.) erişimi sağlamak için kullanılır.
    Yeni bir Activity başlatma, Intent'leri kullanma gibi işler de Context tarafından yapılır.

* Application Context, getApplicationContext() metoduyla uygulamanın herhangi bir yerinden uygulama Context’ini alır, singleton’dır, uygulamayla aynı yaşam süresine sahiptir.
* Activity Context, ActivityName.this yoluyla çağrılır ve Activity ile aynı yaşam süresine sahiptir. Daha çok o Activity içerisindeki objelerde kullanılır. Service’ler de aynı mantıktadır. Activity’nin kendisi Context’i implement eder.
* ContentProvider, herhangi bir Context barındırmaz, sahip olunan getContext() metodu ile uygulama Context’i alınabilir.
* BroadcastReceiver, kendisi herhangi bir Context barındırmaz. onReceive() metoduyla Context alabilir.

## Katkı Sağlayanlar
* [developersancho](https://github.com/developersancho)
* [mucahitkambur](https://github.com/mucahitkambur)
* [mehmettas](https://github.com/mehmettas)
