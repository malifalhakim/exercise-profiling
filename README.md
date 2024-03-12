# Modul 5 : Java *Profiling*

Nama : M.Alif Al Hakim \
NPM : 2206081250 \
Kelas : B 

#### 1. What is the difference between the approach of performance testing with JMeter and profiling with IntelliJ Profiler in the context of optimizing application performance?
> *Performance testing* menggunakan JMeter lebih fokus kepada mengukur kinerja 
> suatu aplikasi dalam lingkup yang lebih luas dan general. *Performance testing* berguna untuk mengukur
> kinerja aplikasi secara keseluruhan yang me-simulasikan keadaan yang dapat terjadi di dunia nyata.\
> Sementara itu, profiling lebih fokus pada mengukur kinerja aplikasi secara spesifik pada *code-level performance*. Profiling bersifat lebih detail
> yang bisa mengidentifikasi bagian kode mana yang belum efisien.

#### 2. How does the profiling process help you in identifying and understanding the weak points in your application?
> Proses profiling memberikan informasi mengenai kinerja tiap bagian dari kode aplikasi. Hal ini membantu saya dalam mengidetifikasi
> bagian kode mana yang perlu saya perbaiki. Profiling sendiri memberikan informasi yang detail tiap method pada code, seperti
> CPU time, Total time, dan Memory Allocation. Informasi-informasi tersebut dapat membantu pengidentifikasian bagian code mana yang
> perlu dilakukan *refactoring*.

#### 3. Do you think IntelliJ Profiler is effective in assisting you to analyze and identify bottlenecks in your application code?
> Menurut saya Intellij Profiler sudah efektif dalam membantu proses profiling. Hal ini dikarenakan proses profiling yang mudah. Selain itu,
> Itellij Profiler juga menyediakan grafik atau menampilkan data dengan cara yang cukup ringkas seperti menggunakan *flame graph*.
> Intellij profiler juga memudahkan saya untuk membandingkan dua hasil profiling sehingga saya dapat dengan mudah membandingkan hasil profiling
> sebelum dan sesudah refactoring.

#### 4. What are the main challenges you face when conducting performance testing and profiling, and how do you overcome these challenges?
> Pada awalnya, saya tidak terlalu memahami bagaimana membaca grafik ataupun tabel pada JMeter ataupun Intellij Profiler. Akan tetapi hal itu, saya atasi
> dengan membaca grafik dan tabel secara seksama dan mencari informasi di internet jika ada hal yang kurang saya pahami. 

#### 5. What are the main benefits you gain from using IntelliJ Profiler for profiling your application code?
> Manfaat utama yang saya rasakan ketika menggunakan IntelliJ profiler adalah mengenai aspek kemudahan dan efektifitas. 
> Intellij Profiler dapat menyediakan sarana untuk melakukan profiling tanpa mendownload aplikasi lain. Selain itu, Intellij
> Profiler juga telah menyediakan grafik atau tabel yang dapat langsung dibaca dan diinterpretasikan oleh penggunanya. Dan juga,
> Intellij profiler tergolong mudah digunakan.

#### 6. How do you handle situations where the results from profiling with IntelliJ Profiler are not entirely consistent with findings from performance testing using JMeter?
> Pada saat melakukan *performance testing* dan *profiling*, saya sendiri tidak mengalami adanya ketidak konsistenan antara JMeter dan Intellij Profiler.
> Akan tetapi, apabila hal itu terjadi saya akan mengulang test dengan beberapa iterasi, Selain itu, saya juga akan memeriksa
> konfigurasi dan testing conditions dari kedua tools tersebut.


#### 7. What strategies do you implement in optimizing application code after analyzing results from performance testing and profiling? How do you ensure the changes you make do not affect the application's functionality?
> Setelah melakukan profiling, saya menganalisis method mana yang memiliki CPU time yang tinggi. Method-method tersebut kemudian
> saya lakukan refactoring.\
> 
> Pada endpoint `all-student`, saya menemukan bahwa method yang perlu untuk dilakuakan *refactoring* adalah method `getAllStudentWithCourse`. Untuk melakukan optimasi pada method tersebut,
> saya mengurangi jumlah panggilan untuk mencari student course dengan Id dan menggunakan method `studentCourseRepository.findAll()` sebagai gantinya. \
> Pada endpoint  `all-student-name`, saya menemukan bahwa method `joinStudentNames` perlu dilakukan refactoring. Untuk melakukan optimasi pada method tersebut,
> saya mengganti proses pembuatan string menggunakan StringBuilder yang lebih efisien.
> Pada endpoint `highest-gpa`, saya melakukan refacotring pada method `findStudentWithHighestGPA`. Untuk mengoptimalkannya,
> saya menggunakan query `SELECT * FROM students ORDER BY gpa DESC LIMIT 1` untuk mengambil mahasiswa dengan IPK tertinggi. Hal ini
> saya terapkan pada bagian StudentRepository.\
> 
> Untuk memastikan hal yang saya ubah tidak merubah fungsi dari aplikasi, saya melakukan perbandingan secara menyeluruh
> pada setiap output dari request yang dikirim. Perbandingan saya lakukan dengan memastikan string yang dikembalikan pada saat sebelum
> dan sesudah refactoring sama persis.


### JMeter Performance Testing Result
#### `all-student-name` endpoint
- JMeter GUI result (Before optimization)
![jmeter-gui-all-student-name-before.png](images%2Fjmeter-gui-all-student-name-before.png)
- JMeter GUI result (After optimization)
![jmeter-gui-all-student-name-after.png](images%2Fjmeter-gui-all-student-name-after.png)
- JMeter Command Line result (Before optimization)
![jmeter-cl-all-student-name-before.png](images%2Fjmeter-cl-all-student-name-before.png)
- JMeter Command Line result (After optimization)
![jmeter-cl-all-student-name-after.png](images%2Fjmeter-cl-all-student-name-after.png)

#### `highest-gpa` endpoint
- JMeter GUI result (Before optimization)
![jmeter-gui-highest-gpa-before.png](images%2Fjmeter-gui-highest-gpa-before.png)
- JMeter GUI result (After optimization)
![jmeter-gui-highest-gpa-after.png](images%2Fjmeter-gui-highest-gpa-after.png)
- JMeter Command Line Result (Before optimization)
![jmeter-cl-highest-gpa-berfore.png](images%2Fjmeter-cl-highest-gpa-berfore.png)
- JMeter Command Line result (After optimization)
![jmeter-cl-highest-gpa-after.png](images%2Fjmeter-cl-highest-gpa-after.png)

#### Kesimpulan
Berdasarkan data diatas terlihat bahwa performa setelah optimasi lebih baik dari pada performa sebelum optimasi.
Hal ini terlihat berdasarkan gambar-gambar diatas baik pengujian melalui GUI ataupun Command Line, waktu eksekusi dari aplikasi 
sesudah optimasi lebih kecil dibandingkan sebelum optimasi. 