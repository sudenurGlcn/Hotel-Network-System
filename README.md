# Otel Ağ Yapısı Sistemi

 ## Giriş
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bu projede 4 katlı bir otelin tüm ağ altyapısının Cisco Packet Tracer uygulamasında simülasyonu oluşturularak yapılmıştır. Otel Oda ve Toplantı Odaları örneklerinden, Resepsiyon, Lobi, Restoran gibi bölümlerden ve Finans, HR, IT, Admin gibi departmanlardan oluşmaktadır. Oteli simgeleyen her bölme için en uygun olduğu düşünülen cihazlar kullanılmıştır. Cihazların birbiriyle etkileşime geçmesi için uygun olan protokoller ve WiFi, Bluetooth bağlantıları kullanılmıştır.
</br></br></br></br>
  
 ## Otelin Genel Bina Planı
![image](https://user-images.githubusercontent.com/88087972/239207098-bb4ee3e5-845e-4d1d-aec0-9319c432d046.png)
<p align="center"><sup>Görsel 1: Otelin Genel Bina Planı</sup></p>
</br></br></br></br>

 ## Kullanılan Cihazların Listesi

| **Adet Sayısı** | **Cihaz** |
| :---: | :---: |
| 14 adet | Akıllı Telefon |
| 8 adet | Laptop |
| 6 adet | Tablet |
| 4 adet | TV |
| 2 adet | Bluetooth Hoparlör |
| 11 adet | IP Phone |
| 4 adet | Printer |
| 5 adet | PC |
| 2 adet | Kahve Makinesi |
| 3 adet | Fan |
| 3 adet | Termostat |
| 11 adet | Yangın Alarmı |
| 2 adet | Klima |
| 4 adet | Duman Dedektörü |
| 1 adet | Güneş Paneli |
| 1 adet | Batarya |
| 4 adet | Access Point |
| 8 adet | Switch |
| 4 adet | Router |
| 4 adet | Home Gateway |

</br>

 ## Cihazların Birbiriyle İletişim Kurması
<ul>
	<li>Her katta bulunan Routerlar birbirine seri DCE kablo ile bağlanmıştır.</li>
	<li>Routerların kendi aralarındaki IPv4 adresleri 10.10.10.0/30, 10.10.10.4/30, 10.10.10.8/30 ve 10.10.10.12/30 şeklindedir.</li>
	<ul><li>Routerların CLI kısmından statik IP ataması yapılmıştır.</li></ul>
	<li>Her katta birer Switch ve Access Point bulunmaktadır.</li>
	<ul><li>Access Point’ler üzerinden WPA2-PSK seçeneği ile kullanıcı adı ve şifre belirlenmiştir. Bu sayede kata ait ilgili cihazlar kendi katlarına ait WiFi’lara bağlanabilmektedir.</li></ul>
	<li>Yönlendirme protokolü olarak OSPF protokolü kullanılmıştır.</li>
	<ul><li>Routerların CLI kısmından “ospf 10” komutu ile protokol tanımlanmıştır.</li></ul>
	<li>Kullanılan tüm cihazlara DHCP ile dinamik adresleme yapılmıştır.</li>
	<ul>
		<li>Routerların CLI kısmından “service dhcp” ve “ip dhcp pool” komutları ile VLAN IPv4 havuzları oluşturulup, kaynak adres olarak Routerların kendi adresleri tanımlanmıştır.</li>
		<li>Switchlerin CLI kısmından Interface FastEthernet komutları ile departmanlara ait cihazlar kendi VLAN’larına ait olarak belirlenip adresleri network adresi olarak kendi Router’ından referans alarak dinamik bir şekilde tanımlanmıştır.</li>
	</ul>
	<li>Kullanılan tüm cihazlar birbiriyle iletişime geçmektedir.</li>
	<ul><li>Switch ve Routerların bağlantı şekli “trunk” moduna alınıp Routerlardan her VLAN için ayrı IP tanımlanması sağlanmıştır.</li></ul>
	<li>Tüm katlardaki telefonların birbiriyle iletişimi Dial-Up teknolojisi ile sağlanmaktadır.</li>
	<ul>
		<li>2811 Routerının bir özelliği olan “telephony-service” kullanılarak IP Phone cihazları arasındaki bağlantı sağlanmıştır. Ayrıca routerlardan “voice vlan” havuzları her kat için ayrı olacak şekilde oluşturulmuştur.</li>
		<li>Switchlerden telefonların “voice vlan” ataması yapılıp IP’leri tanımlanmıştır.</li>
		<li>Son olarak Routerların birbiri ile olan bağlantısı sağlanıp Dial-Up teknolojisi ile katlar arasında telefonlar birbiri ile iletişime geçebilir duruma gelmiştir.</li>
	</ul>
	<li>Home Gateway teknolojisi kullanarak yangın söndürme sistemi ve fan sistemi kurulmuştur.</li>
	<ul>
		<li>Yangın Söndürme Sistemi için yangın söndürücüler ve yangın dedektörü FastEthernet bağlantısı ile Home Gateway’e bağlanmıştır.</li>
		<li>Fan Sistemi için fanlar ve termostatlar WiFi bağlantısı ile Home Gateway’e bağlanmıştır.</li>
		<li>Konfigürasyon için Home Gateway’e bağlı olan bir Akıllı Telefon kullanılmıştır.</li>
	</ul>
	<li>Otelin çatısına konulan güneş paneline batarya bağlanarak güneş enerjisinden faydalanılmaktadır.</li>
</ul>
</br>

![image](https://user-images.githubusercontent.com/88087972/239206004-530b4702-9230-4f37-b28c-1e79dc2154af.png)
<p align="center"><sup>Görsel 2: Otelin Ağ Topolojisi</sup></p>
</br></br></br></br>
	
 ## Projeye Ait Detaylı Kat Planları
 </br>
 
### 1.Kat:
![image](https://user-images.githubusercontent.com/88087972/239249354-137601a7-93ce-42fe-b982-b9dbe2ff4e72.png)
<p align="center"><sup>Görsel 3: 1.Kat Ağ Topolojisi</sup></p></br>

*A. Resepsiyon:*
-	VLAN 10, IP adresi: 192.168.1.0/24
	
*B. Restoran:*
-	VLAN 20, IP adresi: 192.168.2.0/24
	
*C. Lobi:* 
-	VLAN 30, IP adresi: 192.168.3.0/24
</br></br></br></br>

### 2.Kat:
![image](https://user-images.githubusercontent.com/88087972/239248921-bae64d83-7f35-48c3-8312-a2ea0f123f89.png)
<p align="center"><sup>Görsel 4: 2.Kat Ağ Topolojisi</sup></p></br>
 
*A. Oda-101:* 
-	VLAN 40, IP adresi: 192.168.4.0/24

*B. Oda-102:* 
-	VLAN 50, IP adresi: 192.168.5.0/24

*C. Oda-103:* 
-	VLAN 60, IP adresi: 192.168.6.0/24
</br></br></br></br>

### 3.Kat:
![floor3](https://user-images.githubusercontent.com/88087972/239197852-4fc78acf-7417-4d76-b3bc-f71f000e132a.png)
<p align="center"><sup>Görsel 5: 3.Kat Ağ Topolojisi</sup></p></br>

*A. Toplantı Odası:* 
-	VLAN 90, IP adresi: 192.168.9.0/24

*B. İnsan Kaynakları Departmanı:* 
-	VLAN 80, IP adresi: 192.168.8.0/24

*C. Finans Departmanı:*
-	VLAN 70, IP adresi: 192.168.7.0/24
</br></br></br></br>

### 4.Kat:
![floor4](https://user-images.githubusercontent.com/88087972/239198188-9b3319ac-474e-4ed1-a738-54588c061046.png)
<p align="center"><sup>Görsel 6: 4.Kat Ağ Topolojisi</sup></p></br>

*A. Admin:* 
-	VLAN 110, IP adresi: 192.168.11.0/24

*B. IT Departmanı:* 
-	VLAN 100, IP adresi: 192.168.10.0/24

## Otomasyon Sistemi
<p align="center"><img src="https://user-images.githubusercontent.com/88087972/239198431-495fc919-9eaf-4679-b7d3-4fbce33ddf03.png"/></p>
<p align="center"><sup>Görsel 7: IoT Login Ekranı</sup></p></br></br></br></br></br></br></br>

<p align="center"><img src="https://user-images.githubusercontent.com/88087972/239198624-a0e6a60e-655c-49b1-b59a-5b364c84197e.png"/></p>
<p align="center"><sup>Görsel 8: 1.Kat IoT Konfigürasyonu</sup></p></br></br></br></br></br></br>

<p align="center"><img src="https://user-images.githubusercontent.com/88087972/239198640-5adc7777-671b-459a-b612-51a66dc3ff78.png"/></p>
<p align="center"><sup>Görsel 9: 2.Kat IoT Konfigürasyonu</sup></p></br></br></br></br></br></br>

<p align="center"><img src="https://user-images.githubusercontent.com/88087972/239198641-1e92e6ec-4224-464b-ab1b-cd0d26f359f6.png"/></p>
<p align="center"><sup>Görsel 10: 3.Kat IoT Konfigürasyonu</sup></p></br></br></br></br></br></br>

<p align="center"><img src="https://user-images.githubusercontent.com/88087972/239199646-139cfbf3-a772-48bc-834a-b6fa99329e7a.png"/></p>
<p align="center"><sup>Görsel 11: 4.Kat IoT Konfigürasyonu</sup></p></br></br></br></br></br></br>


## Kaynakça
<ul>
	<li>https://gurutechnetworks.otombenard.com/assetsProject/project3</li>
	<li>https://www.youtube.com/watch?v=UrzKYKi8NEM</li>
	<li>https://ipcisco.com/lesson/cisco-packet-tracer-vlan-configuration-example-ccna/</li>
	<li>https://www.youtube.com/watch?v=-nD7jKrsu0o</li>
	<li>https://www.youtube.com/watch?v=PYqIvoPEmRA</li>
	<li>https://www.packettracernetwork.com/tutorials/voipconfiguration.html</li>
	<li>https://www.cisco.com/c/en/us/support/docs/smb/wireless/cisco-small-business-100-series-wireless-access-points/smb5530-set-up-a-wireless-network-using-a-wireless-access-point-wap.html</li>
	<li>https://tr.wikipedia.org/wiki/OSPF</li>
</ul>
 
