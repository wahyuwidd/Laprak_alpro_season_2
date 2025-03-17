# <h1 align="center">Laporan Praktikum Modul 03 <br> Fungsi</h1>
<p align="center">Wahyu Widodo - 103112430011</p>

## Dasar Teori

Fungsi dalam pemrograman adalah sebuah blok kode yang dapat digunakan kembali untuk melakukan tugas tertentu. Fungsi membantu dalam mengorganisir kode, menghindari pengulangan kode, dan membuat program lebih modular. Fungsi juga merupakan satu kesatuan rangkaian instruksi yang memberikan atau menghasilkan suatu nilai dan biasanya memetakkan input ke suatu nilai yang lain. Oleh karena itu, fungsi selalu
menghasilkan/mengembalikan nilai.

## Unguided

### Soal 1

Minggu ini, mahasiswa Fakultas Informatika mendapatkan tugas dari mata kuliah matematika diskrit untuk mempelajari kombinasi dan permutasi. Jonas salah seorang mahasiswa, iseng untuk mengimplementasikannya ke dalam suatu program. Oleh karena itu bersediakah kalian membantu Jonas? (tidak tentunya ya :p)

```go
package main

import "fmt"

func faktorial(n int) int {
	if n == 0 || n == 1 {
		return 1
	}
	hasil := 1
	for i := 2; i <= n; i++ {
		hasil *= i
	}
	return hasil
}

func permutasi(n, r int) int {
	return faktorial(n) / faktorial(n-r)
}

func kombinasi(n, r int) int {
	return faktorial(n) / (faktorial(r) * faktorial(n-r))
}

func main() {
	var a, b, c, d int

	fmt.Print("Masukkan empat bilangan (a b c d): ")
	fmt.Scan(&a, &b, &c, &d)

	Pac := permutasi(a, c)
	Kac := kombinasi(a, c)
	Pbd := permutasi(b, d)
	Kbd := kombinasi(b, d)

	fmt.Println(Pac, Kac)
	fmt.Println(Pbd, Kbd)
}

```

> Output <br>
> ![Screenshot bagian x](tes/modul_03_fungsi/output/soal1.png)

Program ini melakukan perhitungan permutasi dan kombinasi. Terdapat 3 fungsi yang pertama ada fungsi faktorial digunakan untuk menghitung hasil faktor yang digunakan untuk mencari permutasi dan kombinasi. Didalam fungsi faktorial terdapat looping yang digunakan untuk menghitung faktorial menggunakan perulangan dari 2 sampai n dengan mengalikan nya satu persatu. Didalam fungsi permutasi terdapat rumus yaitu n!/n-r! untuk mengitung permutasi nya. Yang terakhir didalm fungsi kombinasi terdapat rumus n!/r!(n-r)! untuk hitung kombinasi nya. Lalu fungsi tidak akan berguna jika tidak di panggil di main program, untuk memanggil nya cukup ketikan nama fungsi beserta parameter yang dibutuh kan, untuk mendapatkan parameter yang dimana adalah input dari user maka ada fmt.Scan lalu panggil fungsi nya kemudian bisa langsung di outputin atau di assign ke variabel lalu baru dioutputin juga bisa.
<br>
### Soal 2

Diberikan tiga buah fungsi matematika yaitu 𝑓 (𝑥) = 𝑥^2, 𝑔 (𝑥) = 𝑥 − 2 dan ℎ (𝑥) = 𝑥 +1. Fungsi komposisi (𝑓𝑜𝑔𝑜ℎ)(𝑥) artinya adalah 𝑓(𝑔(ℎ(𝑥))). Tuliskan 𝑓(𝑥), 𝑔(𝑥) dan ℎ(𝑥) dalam bentuk function.

```go
package main

import "fmt"

func f(x int) int {
	return x * x
}

func g(x int) int {
	return x - 2
}

func h(x int) int {
	return x + 1
}

func fogoh(x int) int {
	return f(g(h(x)))
}

func gohof(x int) int {
	return g(h(f(x)))
}		

func hofog(x int) int {
	return h(f(g(x)))
}

func main() {
	var a, b, c int

	fmt.Print("Masukkan tiga bilangan (a b c): ")
	fmt.Scan(&a, &b, &c)

	fmt.Println(fogoh(a))
	fmt.Println(gohof(b))
	fmt.Println(hofog(c))
}

```

> Output <br>
> ![Screenshot bagian x](tes/modul_03_fungsi/output/soal2.png)

Program ini melakukan perhitungan fungsi matematika. Terdapat 3 fungsi untuk menghitung masing masing fungsi dengan variable f g dan h. lalu terdapat 3 fungsi lagi yaitu (𝑓𝑜𝑔𝑜ℎ)(𝑎),  (𝑔𝑜ℎ𝑜𝑓)(𝑏), dan (ℎ𝑜𝑓𝑜𝑔)(𝑐). kemudian fungsi f, g, dan h dipanggil didalam fungsi (𝑓𝑜𝑔𝑜ℎ)(𝑎),  (𝑔𝑜ℎ𝑜𝑓)(𝑏), dan (ℎ𝑜𝑓𝑜𝑔)(𝑐). lalu dipanggil dimain program. Seperti biasa di main program mendapatkan input pengguna untuk melakukan perhitungan fungsi matematika dengan fungsi fungsi yang sudah di bikin. Disini langsung di outputin jadi ngga perlu di assign ke variable tertentu.
<br>
### Soal 3

[Lingkaran] Suatu lingkaran didefinisikan dengan koordinat titik pusat (𝑐𝑥, 𝑐𝑦) dengan radius 𝑟. Apabila diberikan dua buah lingkaran, maka tentukan posisi sebuah titik sembarang (𝑥, 𝑦) berdasarkan dua lingkaran tersebut.

```go
package main

import (
	"fmt"
	"math"
)

func jarak(a, b, c, d float64) float64 {
	dx := (a - c) * (a - c)
	dy := (b - d) * (b - d)
	return math.Sqrt(dx + dy)
}

func didalam(cx, cy, r, x, y float64) bool {
	return jarak(cx, cy, x, y) <= r
}

func main() {
	var cx1, cy1, r1 float64
	var cx2, cy2, r2 float64
	var x, y float64

	fmt.Scan(&cx1, &cy1, &r1)
	fmt.Scan(&cx2, &cy2, &r2)
	fmt.Scan(&x, &y)

	dalam1 := didalam(cx1, cy1, r1, x, y)
	dalam2 := didalam(cx2, cy2, r2, x, y)

	if dalam1 && dalam2 {
		fmt.Println("Titik di dalam lingkaran 1 dan 2")
	} else if dalam1 {
		fmt.Println("Titik di dalam lingkaran 1")
	} else if dalam2 {
		fmt.Println("Titik di dalam lingkaran 2")
	} else {
		fmt.Println("Titik di luar lingkaran 1 dan 2")
	}
}

```

> Output <br>
> ![Screenshot bagian x](tes/modul_03_fungsi/output/soal3.png)

Program ini menentukan apakah sebuah titik berada di dalam satu atau dua lingkaran menggunakan konsep jarak Euclidean untuk mengecek apakah titik berada di dalam suatu lingkaran. Nah disini terdapat 2 fungsi yaitu fungsi jarak dan didalam. Fungsi jarak digunakan untuk menghitung **jarak Euclidean** antara dua titik (a,b)(a, b)(a,b) dan (c,d)(c, d)(c,d). Lalu menggunakan package math untuk mengambil akar dari jumlah kuadrat kedua selisih tersebut. Fungsi kedua yaitu fungsi didalam digunakan untuk mengecek apakah titik **(x, y)** berada di dalam lingkaran dengan pusat **(cx, cy)** dan jari-jari **r**. Jika jarak titik ke pusat lingkaran lebih kecil atau sama dengan r, maka titik berada di dalam lingkaran (true).
Jika jarak lebih besar dari r, titik berada di luar lingkaran (false). Lalu masuk ke main program meminta pengguna memasukkan:
    - Pusat **lingkaran 1** `(cx1, cy1)` dan jari-jarinya `r1`
    - Pusat **lingkaran 2** `(cx2, cy2)` dan jari-jarinya `r2`
    - Koordinat titik `(x, y)`
Lalu program memeriksa apakah titik `(x, y)` berada di dalam **lingkaran 1** dan **lingkaran 2** menggunakan fungsi didalam. Dan kemudian program melakukan perbandingan: 
Jika titik berada di kedua lingkaran, program mencetak "Titik di dalam lingkaran 1 dan 2".
Jika titik hanya di dalam lingkaran 1, program mencetak "Titik di dalam lingkaran 1".
Jika titik hanya di dalam lingkaran 2, program mencetak "Titik di dalam lingkaran 2".
Jika titik tidak berada di dalam kedua lingkaran, program mencetak "Titik di luar lingkaran 1 dan 2".
