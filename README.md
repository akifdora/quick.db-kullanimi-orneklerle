# quick.db-kullanimi-orneklerle

new table
Database'yi kullanırken verilerinizi ayırmanızı sağlar.

const akifdata = new db.table('akifdata')
akifdata.set(`Para_${message.author.id}`,100) // Bir kullanıcının para verisini akifdata kullanımıyla 100 olarak ayarladık.
akifdata.get(`Para_${message.author.id}`) // 100 olarak ayarladığımız verinin çıktısını verir.
db.get(`${message.author.id}`) // Tanımsızdır, nedeni ise data işlemlerini kullanmak için akifdata ismini tanımlamış olmamdır.


add
Datanıza sayısal veriler eklemenizi sağlar.

db.add(`Para_${message.author.id}`,5) // Bir kullanıcının para verisine 5 ekledik. 100 olan veri artık 105 olacaktır.



subtract
Datanızdan sayısal verileri çıkarmanızı sağlar.

db.add(`Para_${message.author.id}`,5) // Bir kullanıcının para verisinden 10 çıkarttık. 105 olan veri artık 95 olacaktır.



delete
Verinizi veritabanından silmenizi sağlar.

db.delete(`Para_${message.author.id}`) // Kullanıcının parasını veritabanından sildik. Artık bu veriyi çekmeye çalıştığımızda null değeri gelecektir.



set
Datanızdaki veriyi direkt olarak ayarlamanızı sağlar.

db.set(`Para_${message.author.id}`,2) // Bir kullanıcının para verisini 50 olarak ayarladık. null olan veri artık 50 olacaktır.
db.set(`İsim_${message.author.id}`,'Dora') // Bir kullanıcının isim verisini Akif olarak ayarladık. null olan veri artık Akif olacaktır.



get / fetch
Datanızdaki veriyi döndürmenizi, çekmenizi sağlar.

db.get(`Para_${message.author.id}`) // Bir kullanıcının para verisini döndürür. 50 olarak ayarladığımız paranın çıktısı ekrana 50 olarak gelir.
db.fetch(`İsim_${message.author.id}`) // => Bir kullanıcının isim verisini döndürür. Akif olarak ayarladığımız isim ekrana Akif olarak gelir.



has / exists
Datada verinin var olup olmadığını kontrol etmenizi sağlar.

db.has(`Para_${message.author.id}`) // Boolean değerler oldukları için yalnızca true veya false çıktısı verir. false = veri yok / true = veri var
db.exists(`Para_${message.author.id}`) // Boolean değerler oldukları için yalnızca true veya false çıktısı verir. false = veri yok / true = veri var



push
Veriyi dizi (array) olarak kullanıp var olan dizinin içine ekleme yapar.

db.push(`Envanter_${message.author.id}`,'kılıç') // Şu anda verimiz array olmadığı için yeni bir array oluşturdu ve kılıcı onun içine yazdırdı. Verimiz artık ['kılıç'] şeklinde ekranda görünecek.
db.push(`Envanter_${message.author.id}`,'kalkan') // Verimizin arrayinde şu an kılıç olduğu için yanına kalkan ekledi. Verimiz artık ['kılıç','kalkan'] şeklinde ekranda görünecek.



push ile dizi içerisinden veri silme

const silmefiltresi = db.get(`Envanter_${message.author.id}`).filter(x => x !== 'kılıç') // Verimizde kılıç olmayan verileri filtreledik ve çıktıyı aldık.
db.set(`Envanter_${message.author.id}`, silmefiltresi) // Verimizi filtrelenmiş haline ayarladık son çıktımız ['kılıç','kalkan'] artık ['kalkan'] oldu.
