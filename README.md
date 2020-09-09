# Style_-_Theme
### Pengupulan Modul Style And Theme
#### Teori <br>
Pada modul ini, Anda akan mempelajari prinsip desain yang ada di Android. Anda juga akan mempelajari bagaimana menerapkan struktur dan tampilan view dalam sebuah berkas style. 
Prinsip dasar dalam merancang antarmuka aplikasi Android harus mematuhi kaidah yang ditetapkan oleh Design Guideline. Guideline ini dibuat oleh tim Android di Google. Beberapa prinsipnya adalah:
<br>
1.	Menampilkan informasi yang hanya dibutuhkan.
2.	Jika aplikasi meminta izin pengguna untuk melakukan sebuah aksi, maka pengembang harus menyediakan mekanisme untuk membatalkan izin tersebut.
3.	Lakukan interupsi jika diperlukan.
4.	Menggunakan teks secara singkat. Gunakan gambar untuk menjelaskan informasi secara lebih deskriptif.
5.	Jaga data pengguna.
6.	Permudah pengguna untuk melakukan sesuatu yang penting secara cepat.
7.	Jika terlihat sama, maka perilaku haruslah sama.
8.	Bantu pengguna untuk membuat keputusan tapi tetap biarkan pengguna menentukan keputusannya. <br>

#### Best Practice
Terdapat beberapa langkah terbaik (best practice) yang harus diperhatikan ketika mengembangkan sebuah aplikasi Android, di antaranya: <br>
1.	Desain yang baik untuk performa aplikasi
Aplikasi yang dirancang dengan baik harus dapat dijalankan dengan cepat dan jika terdapat proses yang memakan waktu, maka jalankan di background dan asynchronous.
2.	Desain yang baik agar aplikasi dapat bersifat responsif
Berikan feedback ke pengguna terhadap aksi yang dilakukannya. Contohnya, jika pengguna menekan sebuah tombol, maka aplikasi harus menampilkan efek tekan.
3.	Desain yang mengakomodasi kebutuhan informasi pengguna
Aplikasi Anda harus menampilkan informasi yang dibutuhkan pengguna. Bila diperlukan, aplikasi perlu menampilkan informasi terakhir yang diperoleh, sehingga pengguna tidak perlu lagi menunggu aplikasi memuat data dari server.
4.	Desain untuk optimasi pengunaan baterai
Usahakan agar aplikasi menggunakan daya baterai yang kecil. Minimalisir penggunaan background service yang tidak perlu. Berhentikan semua listener jika aplikasi tidak sedang dijalankan. Manfaatkan alarmmanager dan jobscheduler jika memang terdapat task yang harus dilakukan secara berkala.
5.	Desain untuk efisiensi pengunaan koneksi jaringan
Aplikasi yang baik adalah yang efisien dalam memanfaatkan koneksi ke jaringan internet. Ia memilah-milah task mana yang perlu dijalankan saat perangkat pengguna terhubung ke wifi (unmetered network) atau pun network lain. Penggunaan koneksi jaringan yang baik akan menjadi hal wajib jika aplikasi Anda ingin tetap digunakan oleh pengguna.
<br>
Nilai yang bagus pada poin tampilan akan mendukung kualitas fungsi aplikasi yang dibuat. Pengguna akan mempertahankan aplikasi Anda dan tetap menggunakannya selama aplikasi dibutuhkan dan memenuhi poin-poin di atas. <br>
Kembali pada topik style dan theme. Jika Anda pernah mengembangkan sebuah aplikasi berbasis web, maka sudah pasti tidak asing lagi dengan CSS (Cascading Style Sheet). Ia mengatur tampilan dari sebuah halaman website. Pendekatan yang serupa juga berlaku di Android. Inilah yang dinamakan style. <br>
Style merupakan sebuah kumpulan properti yang dibutuhkan untuk mendefinisikan bagaimana sebuah komponen view dan layar jendela (bisa activity maupun fragment) ditampilkan. Contoh properti ini adalah height, width, background_color. <br>
Style terdefinisi dalam file xml sendiri. Anda bisa menemukannya di res →  values  →  styles.xml. <br>
Sebagai contoh, Anda memiliki sebuah textview yang berisi berbagai atribut seperti contoh kode di bawah ini. Textview ini berguna untuk menampilkan konten dari detail informasi yang terdapat di keseluruhan aplikasi. <br>
1.	<TextView
2.	android:layout_width="match_parent"
3.	android:layout_height="wrap_content"
4.	android:textColor="#00FF00"
5.	android:typeface="monospace"
6.	android:text="@string/hello" />

Sangat tidak efektif jika kita melakukan copy paste dari satu layout xml ke layout xml lainnya. Kita dapat menyederhanakan hal tersebut menjadi: <br>
1.	<TextView
2.	style="@style/CodeFont"
3.	android:text="@string/hello" />

Attribute layout_width, layout_height, textcolor, dan typeface bisa kita pindahkan menjadi sebuah style sendiri untuk textview tersebut dan dapat digunakan kembali untuk semua obyek textview sejenis. <br>
1.	<?xml version="1.0" encoding="utf-8"?>
2.	<resources>
3.	<style name="CodeFont" parent="@android:style/TextAppearance.Medium">
4.	    <item name="android:layout_width">match_parent</item>
5.	    <item name="android:layout_height">wrap_content</item>
6.	    <item name="android:textcolor">#00FF00</item>
7.	    <item name="android:typeface">monospace</item>
8.	</style>
9.	</resources>

Beberapa aturan yang harus diperhatikan ketika kita menggunakan styles yaitu: <br>
1.	Semua style yang dibuat harus berada dalam tag resources.<br>
2.	Semua style yang ingin didefinisikan harus berada dalam tag style.<br>
1.	<style name="CodeFont" parent="@android:style/TextAppearance.Medium"><br>

Name      :    Nama dari style yang Anda buat. <br>
Parent    :     Nilai style yang akan mewarisi style (termasuk attribute di dalamnya) yang telah ada, umumnya bawaan dari sdk ataupun platform. <br>
Style yang diwarisi akan dapat diubah dan ditambahkan atributnya dalam style baru yang Anda buat. Android sudah menyediakan beragam style yang bisa Anda gunakan untuk beragam tampilan.<br>
3.	Semua atribut yang didefinisikan dalam sebuah style harus berada dalam tag item.
1.	<item name="android:layout_width">match_parent</item>

Name                  :    Nama atribut yang ingin didefinisikan.<br>
Match_parent :    Nilai dari atribut tersebut.<br>
Andaikan dalam satu kasus Anda ingin membuat turunan dari style yang telah Anda buat. Misalnya Anda ingin membuat style CodeFont berwarna merah, Anda dapat melakukannya dengan cara berikut ini:
1.	<style name="CodeFont.Red">
2.	<item name="android:textColor">#FF0000</item>
3.	</style>
atau berwarna merah dan juga dengan ukuran yang besar menjadi seperti ini :
1.	<style name="CodeFont.Red">
2.	<item name="android:textColor">#FF0000</item>
3.	<item name="android:textSize">30sp</item>
4.	</style>
Mudah bukan? Anda baru saja belajar tentang bagaimana sebuah style dibuat dan diimplementasikan. Selanjutnya Anda akan mempelajari theme.<br>
Theme atau tema itu sendiri merupakan sebuah style yang diterapkan khusus untuk activity dan application pada berkas AndroidManifest.xml. Pada proyek sebelumnya, kita mendefinisikannya dengan cara berikut ini:<br>
1.	android:theme="@style/AppTheme"
Di mana AppTheme pada styles.xml berisi :
1.	<resources>
2.	<style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
3.	    <!-- Customize your theme here. -->
4.	    <item name="colorPrimary">@color/colorPrimary</item>
5.	    <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
6.	    <item name="colorAccent">@color/colorAccent</item>
7.	</style>
8.	</resources>
Sebuah styles yang inherit ke tema AppCompat untuk varian light dan memiliki DarkActionBar. Semua nilai pada atribut terdapat pada berkas colors.xml yang berisi.
1.	<resources>
2.	    <color name="colorPrimary">#3F51B5</color>
3.	    <color name="colorPrimaryDark">#303F9F</color>
4.	    <color name="colorAccent">#FF4081</color>
5.	</resources>
<br>
### RESULT
![Alt Text](https://github.com/adam033/Style_-_Theme/blob/master/Screenshot%20(346).png)
![Alt Text](https://github.com/adam033/Style_-_Theme/blob/master/Screenshot%20(347).png)

#### SEMOGA BERMANFAAT , TERIMA KASIH (SELENGKAPNYA CEK MODUL) :)




