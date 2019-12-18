# Android Geliştiricilerin Bilmesi(en azından fikir sahibi olması) Gereken Core Bilgiler

#### Prepared by [developersancho](https://github.com/developersancho) who is having experience and work on Android Development.

## Sorular

#### ANR Nedir ?
    ANR, "(A)pplication (N)ot (R)esponding" anlamına gelir. UI thread'de uzun süren(5 saniye içerisinde yanıt alınamayan)
    işlemlerde Android isletim sistemi tarafından gösterilen bir dialogdur.

#### Context Nedir ?
    Context, uygulamanin herhangi bir zamandaki durumunu tutan bir objedir.
    Uygulamadaki kaynaklara referans olarak her yerden erişmemizi saglayan Android isletim sistemi tarafindan implement edilmis bir Interface'dir.
    Uygulamanin /res klasorunde bulunan kaynaklara (stringler, resim dosyalari vs.) erisimi saglamak icin kullanilir.
    Yeni bir Activity baslatma, Intent'leri kullanma gibi isler de Context tarafindan yapilir.
    
* Application Context, getApplicationContext() metoduyla uygulamanın herhangi biryerinden uygulama Context’ini alınır, singleton’dır, uygulamayla aynı yaşam süresine sahiptir.
* Activity Context, ActivityName.this yoluyla çağrılır ve Activity ile aynı yaşam süresine sahiptir. Daha çok o Activity içerisindeki objelerde kullanılır. Service’ler de aynı mantıktadır. Activity’nin kendisi Context’i implement eder.
* ContentProvider, herhangi bir Context barındırmaz lakin sahip olunan getContext() metodu ile uygulama Context’i alınabilir.
* BroadcastReceiver, kendisi herhangi bir Context barındırmaz. onReceive() metoduyla Context alabilir.

## Katkı Sağlayanlar
* [developersancho](https://github.com/developersancho)
* [mucahitkambur](https://github.com/mucahitkambur)
* [mehmettas](https://github.com/mehmettas)
