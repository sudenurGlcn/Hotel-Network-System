# Otel Ağ Yapısı Sistemi
## Özet
### Bu projede 4 katlı bir otelin tüm ağ altyapısının Cisco Packet Tracer uygulamasında simülasyonu oluşturularak yapılmıştır. Otel Oda ve Toplantı Odaları örneklerinden, Resepsiyon, Lobi, Restoran gibi bölümlerden ve Finans, HR, IT, Admin gibi departmanlardan oluşmaktadır. Oteli simgeleyen her bölme için en uygun olduğu düşünülen cihazlar kullanılmıştır. Cihazların birbiriyle etkileşime geçmesi için uygun olan protokoller ve WiFi, Bluetooth bağlantıları kullanılmıştır.
### otelin Genel Bina Planı
![image](https://github.com/sudenurGlcn/Hotel-Network-System/assets/114651615/2a598a65-3408-4e18-81db-bfc45384d7dc)
### Cihazların Birbiriyle İletişim Kurması
-	Her katta bulunan Routerlar birbirine seri DCE kablo ile bağlanmıştır.
* Routerların kendi aralarındaki IPv4 adresleri 10.10.10.0/30, 10.10.10.4/30, 10.10.10.8/30 ve 10.10.10.12/30 şeklindedir.
* Routerların CLI kısmından statik IP ataması yapılmıştır.
*	Her katta birer Switch ve Access Point bulunmaktadır.
* Access Point’ler üzerinden WPA2-PSK seçeneği ile kullanıcı adı ve şifre belirlenmiştir. Bu sayede kata ait ilgili cihazlar kendi katlarına ait WiFi’lara bağlanabilmektedir.
*	Yönlendirme protokolü olarak OSPF protokolü kullanılmıştır.
*	Routerların CLI kısmından “ospf 10” komutu ile protokol tanımlanmıştır.
*	Kullanılan tüm cihazlara DHCP ile dinamik adresleme yapılmıştır.
*	Routerların CLI kısmından “service dhcp” ve “ip dhcp pool” komutları ile VLAN IPv4 havuzları oluşturulup, kaynak adres olarak Routerların kendi adresleri tanımlanmıştır.
*	Switchlerin CLI kısmından Interface FastEthernet komutları ile departmanlara ait cihazlar kendi VLAN’larına ait olarak belirlenip adresleri network adresi olarak kendi Router’ından referans alarak dinamik bir şekilde tanımlanmıştır.
* Kullanılan tüm cihazlar birbiriyle iletişime geçmektedir.
*	Switch ve Routerların bağlantı şekli “trunk” moduna alınıp Routerlardan her VLAN için ayrı IP tanımlanması sağlanmıştır.
*	Tüm katlardaki telefonların birbiriyle iletişimi Dial-Up teknolojisi ile sağlanmaktadır.
*	2811 Routerının bir özelliği olan “telephony-service” kullanılarak IP Phone cihazları arasındaki bağlantı sağlanmıştır. Ayrıca routerlardan “voice vlan” havuzları her kat için ayrı olacak şekilde oluşturulmuştur.
*	Switchlerden telefonların “voice vlan” ataması yapılıp IP’leri tanımlanmıştır.
*	Son olarak Routerların birbiri ile olan bağlantısı sağlanıp Dial-Up teknolojisi ile katlar arasında telefonlar birbiri ile iletişime geçebilir duruma gelmiştir.
*	Home Gateway teknolojisi kullanarak yangın söndürme sistemi ve fan sistemi kurulmuştur.
*	Yangın Söndürme Sistemi için yangın söndürücüler ve yangın dedektörü FastEthernet bağlantısı ile Home Gateway’e bağlanmıştır.
*	Fan Sistemi için fanlar ve termostatlar WiFi bağlantısı ile Home Gateway’e bağlanmıştır.
*	Konfigürasyon için Home Gateway’e bağlı olan bir Akıllı Telefon kullanılmıştır.
*	Otelin çatısına konulan güneş paneline batarya bağlanarak güneş enerjisinden faydalanılmaktadır.
	![image](https://github.com/sudenurGlcn/Hotel-Network-System/assets/114651615/523afa18-bf25-45c6-8a24-6274211b8152)
 ## Projeye Ait Detaylı Kat Planı
 ### 1.Kat:
 ![image](https://github.com/sudenurGlcn/Hotel-Network-System/assets/114651615/4dded1c7-9e6c-4a4f-88a6-673efe0923c0)
 * A. Resepsiyon:
 *	VLAN 10, IP adresi: 192.168.1.0/24
 * B. Restoran:
 * VLAN 20, IP adresi: 192.168.2.0/24
 * C. Lobi: 
 *	VLAN 30, IP adresi: 192.168.3.0/24
 ### 2.Kat:
 ![image](https://github.com/sudenurGlcn/Hotel-Network-System/assets/114651615/96253b48-4f57-498a-a27e-00ae8dd7a46c)

 
 

 







 
