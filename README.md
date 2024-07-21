Golang ile RESTful Todo List API'si
Giriş
Golang (ya da Go), Google tarafından geliştirilen açık kaynaklı, statik tipli bir programlama dilidir. Golang, özellikle yüksek performanslı ve ölçeklenebilir web uygulamaları geliştirmek için tercih edilir. Bu makalede, Golang kullanarak basit bir RESTful Todo List API'si nasıl oluşturulur adım adım anlatılacaktır.

Proje Kurulumu
Öncelikle, projemiz için bir dizin oluşturuyor ve bu dizin içinde çalışıyoruz. Golang modülünü başlatarak projeye ait bağımlılıkları yönetebilir hale geliyoruz. go mod init komutu ile proje dizinimizi bir Go modülü olarak başlatıyoruz.


Ana Uygulama Dosyasının Oluşturulması
Ana uygulama dosyamız main.go ismiyle oluşturulacak. Bu dosyada temel HTTP işlemlerini gerçekleştirecek fonksiyonlar ve veri yapıları tanımlanacak. main.go dosyası, API'nin tüm işlevselliğini içerecektir.

Temel Yapılar ve İşlevler
Proje içinde Todo öğelerini temsil eden bir yapı ve bu yapı üzerinde CRUD (Create, Read, Update, Delete) işlemlerini gerçekleştirecek fonksiyonlar tanımlanır. Todo yapısı, her görevi tanımlayan ID, Title, ve Status alanlarını içerir. Bu yapının bir dilimi (slice) olan todos ve her yeni görev için benzersiz bir kimlik (ID) sağlayacak bir sayaç nextID tanımlanır.

CRUD İşlemleri
Tüm Görevleri Listeleme (GET /todos)
Bu işlev, tüm Todo öğelerini JSON formatında döndürür. İstemciden gelen GET isteğini işler ve mevcut tüm görevleri döner.

Belirli Bir Görevi Getirme (GET /todos/{id})
Belirli bir görevin ID'sini kullanarak o görevi döner. Eğer görev bulunamazsa, 404 Not Found hatası döner.

Yeni Görev Oluşturma (POST /todos)
İstemciden gelen JSON formatındaki veriyi alır ve yeni bir Todo öğesi olarak kaydeder. Yeni görevin ID'si otomatik olarak atanır ve görevler listesine eklenir.

Mevcut Bir Görevi Güncelleme (PUT /todos/{id})
Belirli bir ID'ye sahip mevcut bir görevi günceller. Eğer görev bulunamazsa, 404 Not Found hatası döner. Güncellenmiş görev, yeni verilerle değiştirilir ve görevler listesinde güncellenir.

Görev Silme (DELETE /todos/{id})
Belirli bir ID'ye sahip görevi siler. Eğer görev bulunamazsa, 404 Not Found hatası döner. Silme işlemi başarılı olduğunda, sunucu 204 No Content cevabı döner.

Uygulamayı Çalıştırma
Geliştirilen bu fonksiyonlar, bir HTTP router kullanarak HTTP istekleri ile ilişkilendirilir. Bu projede, Golang için popüler bir router kütüphanesi olan gorilla/mux kullanılır. gorilla/mux kütüphanesi, esnek ve güçlü bir URL yönlendirme yapısı sunar.

Uygulama, 8080 portunda dinlemeye başlar ve belirtilen URL'lere gelen HTTP isteklerini ilgili fonksiyonlara yönlendirir. Bu sayede, istemciler belirtilen URL'ler üzerinden Todo List API'si ile etkileşime geçebilir.

Sonuç
Bu makalede, Golang kullanarak basit bir RESTful Todo List API'si oluşturmanın temelleri anlatılmıştır. Proje, Golang'ın esnekliği ve performansı ile birlikte gorilla/mux kütüphanesinin gücünü kullanarak temel CRUD işlemlerini gerçekleştiren bir API sunmaktadır. Bu temel yapı, daha gelişmiş özellikler eklemek için genişletilebilir ve ölçeklenebilir bir yapıya sahiptir. Authentication, validation ve error handling gibi konuları inceleyerek API'nizi daha güvenli ve kullanıcı dostu hale getirebilirsiniz.
