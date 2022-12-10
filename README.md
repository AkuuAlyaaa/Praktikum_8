NAMA      : ALYA SEFHIA EKA PUTRI

NIM       : 312210108

KELAS     : TI.22.B1

# Latihan OOP pada python menggunakan class dan menginstansiasi sebuah class lalu membuat program crud sederhana dengan class

1. Pertama kita buat buat folder Praktikum_8 dan didalam kita buat file bernama Praktikum8.py

    ![1](https://user-images.githubusercontent.com/115520278/206855676-92b171c3-5135-4e78-98c1-e387f45a0f54.PNG)

2. Kita akan buat program crud sederhana dan berikut flowchart dan class diagram program yang akan dibuat.

     flowchart :
  
     ![2](https://user-images.githubusercontent.com/115520278/206855733-76cf9347-51d3-4836-8048-4a54cd83b88b.png)
  
     class diagram :
  
     ![3](https://user-images.githubusercontent.com/115520278/206855771-dcf8d492-2b41-4379-88fd-2e9e5f9ccd95.png)

3. Lalu buka file Praktikum8.py dan masukan codingan sebagai berikut, lalu run dengan mengetikan perintah berikut diterminal python Praktikum8.py:

            # import tabulate
        from tabulate import tabulate

        # Alya Sefhia Eka Putri
        # TI.22.B1

        # Membuat class dengan nama Mahasiswa


        class Mahasiswa:
            def __init__(self):
                # membuat properti dataMahasiswa bertipe dictionary
                self.dataMahasiswa = {
                    'No' : [],
                    'Nim' : [],
                    'Nama' : [],
                    'Tugas' : [],
                    'Uts' : [],
                    'Uas' : [],
                    'Nilai Akhir' : []
                }

            # method untuk menampilkan data
            # self merupakan parameter untuk mengakses properti,
            def tampilkan(self):
                print("Berikut data yang ada")
                print(tabulate(self.dataMahasiswa, headers=[
                    'No', 'Nim' , 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))

            # method untuk menmbahkan data

            def tambah(self, no):
                # menginput data
                nim = int(input("Masukkan NIM : "))
                nama = input("Masukkan Nama : ")
                tugas = int(input("Masukkan nilai tugas : "))
                uts = int(input("Masukkan nilai UTS : "))
                uas = int(input("Masukkan nilai UAS : "))
                nilai_akhir = (tugas * 30 / 100) + (uts * 35 / 100) + (uas * 35 / 100)
                # menambahkan data
                self.dataMahasiswa['No'].append(no)
                self.dataMahasiswa['Nim'].append(nim)
                self.dataMahasiswa['Nama'].append(nama)
                self.dataMahasiswa['Tugas'].append(tugas)
                self.dataMahasiswa['Uts'].append(uts)
                self.dataMahasiswa['Uas'].append(uas)
                self.dataMahasiswa['Nilai Akhir'].append(nilai_akhir)
                print('Data berhasil di tambahkan.')
                # print(tabulate(dataMahasiswa, headers=[
                #       'nim', 'nama', 'tugas', 'uts', 'uas', 'Nilai Akhir'], tablefmt="fancy_grid"))

            # method untuk mengedit data

            def ubah(self, nama):
                # cek jika ada nama tersebut di dataMahasiswa
                if nama in self.dataMahasiswa['Nama']:
                    # cari posisi indexnya lalu simpan di nimIndex
                    namaIndex = self.dataMahasiswa['Nama'].index(nama)
                    print("Pilih data yang mau di edit : ")
                    # perulangan mengedit data dalam bentuk pilihan
                    while True:
                        editApa = int(input(
                            "(1) Nim, \n (2) Nama, \n (3) Nilai Tugas, \n (4) Nilai Uts, \n (5) Nilai Uas, \n (0) Save perubahan & exit \n : "))
                        print("")

                        if editApa == 1:
                            # merubah nim
                            newNim = int(input("Masukkan Nim :"))
                            self.dataMahasiswa['Nim'][namaIndex] = newNim
                        elif editApa == 2:
                            # merubah nama
                            newNama = input("Masukkan Nama :")
                            self.dataMahasiswa['Nama'][namaIndex] = newNama
                        elif editApa == 3:
                            # merubah nilai tugas dan nilai akhir
                            newTugas = int(input("Masukkan nilai tugas : "))
                            nilai_akhir = (newTugas * 30 / 100) + (self.dataMahasiswa['Uts'][namaIndex] * 35 / 100) + (
                                self.dataMahasiswa['Uas'][namaIndex] * 35 / 100)
                            self.dataMahasiswa['Tugas'][namaIndex] = newTugas
                            self.dataMahasiswa['Nilai Akhir'][namaIndex] = nilai_akhir
                        elif editApa == 4:
                            # merubah nilai uts dan nilai akhir
                            newUts = int(input("Masukkan nilai Uts :"))
                            nilai_akhir = (self.dataMahasiswa['Tugas'][namaIndex] * 30 / 100) + (newUts * 35 / 100) + (
                                self.dataMahasiswa['Uas'][namaIndex] * 35 / 100)
                            self.dataMahasiswa['Uts'][namaIndex] = newUts
                            self.dataMahasiswa['Nilai Akhir'][namaIndex] = nilai_akhir
                        elif editApa == 5:
                            # merubah nilaiuas dan nilai akhir
                            newUas = int(input("Masukkan nilai uas : "))
                            nilai_akhir = (self.dataMahasiswa['Tugas'][namaIndex] * 30 / 100) + (self.dataMahasiswa['Uts'][namaIndex] * 35 / 100) + (
                                newUas * 35 /100)
                            self.dataMahasiswa['Uas'][namaIndex] = newUas
                            self.dataMahasiswa['Nilai Akhir'][namaIndex] = nilai_akhir
                        elif editApa == 0:
                            print('Perubahan data berhasil di simpan.')
                            break
                else:
                    print('Data tidak di temukan.')

            # fungsi untuk menghapus data

            def hapus(self, nama):
                if nama in self.dataMahasiswa['Nama']:
                    namaIndex = self.dataMahasiswa['Nama'].index(nama)
                    # menghapus data berdasarkan position index pada nama
                    del self.dataMahasiswa['No'][namaIndex]
                    del self.dataMahasiswa['Nim'][namaIndex]
                    del self.dataMahasiswa['Nama'][namaIndex]
                    del self.dataMahasiswa['Tugas'][namaIndex]
                    del self.dataMahasiswa['Uts'][namaIndex]
                    del self.dataMahasiswa['Uas'][namaIndex]
                    del self.dataMahasiswa['Nilai Akhir'][namaIndex]     
                    print("Data berhasil di hapus.")
                else:
                    print("Data tidak di temukan.")

        # fungsi untuk mencari data


        # melkukan perulangan menggunakan while sampai user menekan huruf  Q perulangan akan
        no = 0
        # instansiasi class mahasiswa dengan nama instanceMhs
        instanceMhs = Mahasiswa()

        # melakukan perulangan sampai kondisi tertentu terpenuhi perulangan dan berhenti
        while True:
            # opsi input pilihan C,R,U,D,Q
            tanya = input(
                "(C) Menambah data, \n (R) Melihat semua data, \n (U) Update data, \n (D) Menghapus data, \n (F) Mencari data, \n (Q) Keluar program : ")
            if tanya == "C":
                # melakukan perulangan hingga user memilih n maka perulangan akan berhenti
                while True:
                    no += 1
                    # memanggil fungsi tambah data dan memparsing data no
                    instanceMhs.tambah(no)
                    tambahDataLagi = input("Tambah data lagi ? (y/n) : ")
                    if tambahDataLagi == 'n':
                        break
                # jika tanya == R maka lihat data
            elif tanya == "R":
                # menampilan data dalam bentuk table menggunakan package tabulate
                instanceMhs.tampilkan()
                print("")
                # jika tanya == U maka edit data
            elif tanya == "U":
                print(tabulate(instanceMhs.dataMahasiswa, headers=[
                    'No', 'Nim', 'Nama', 'Tugas', 'Uts', 'Uas', 'Nilai Akhir'], tablefmt="fancy_grid"))
                nama = input("Masukkan nama yang mau di edit : ")
                print("")
                instanceMhs.ubah(nama) 
                # jika tanya == D maka hapus data
            elif tanya == "D":
                print(tabulate(instanceMhs.dataMahasiswa, headers=[
                    'No', 'Nim', 'Nama', 'Tugas', 'Uts', 'Uas', 'Nilai Akhir'], tablefmt="fancy_grid"))
                nama = input("Masukkan nama yang mau di hapus : ")
                print("")
                instanceMhs.hapus(nama) 
                # jika tanya== Q maka keluar dari program
            elif tanya == "Q":
                print("")
                print("Anda telah keluar dari program.")
                break
                
    dan Berikut hasilnya :

 - Jika memilih opsi C = menambah data maka akan tampil sebagai berikut :
  
   ![4](https://user-images.githubusercontent.com/115520278/206856271-77daba71-e275-4b57-9eee-ed165af30683.PNG)

 - Jika memilih opsi R = Melihat semua data maka akan tampil sebagai berikut :
  
   ![5](https://user-images.githubusercontent.com/115520278/206856293-d955a15a-2835-434f-9105-54387ea564d5.PNG)

 - Jika memilih opsi U = mengupdate data maka akan tampil sebagai berikut :
  
   ![6](https://user-images.githubusercontent.com/115520278/206856330-a0c92202-a905-4859-87fb-3d9c2bceadf7.PNG)

 - Jika memilih opsi D = Menghapus data maka akan tampil sebagai berikut :

   ![7](https://user-images.githubusercontent.com/115520278/206856340-70a6e26b-661e-40c3-bfed-e97ca63dfb41.PNG)

 - Jika memilih opsi Q = Keluar Program maka akan tampil sebagai berikut :

   ![8](https://user-images.githubusercontent.com/115520278/206856367-e4a1a978-f6d9-416e-a337-3dab6d790fe9.PNG)

  Seperti itulah program crud sederhana yang kita buat, menggunakan class pada python

  Terimakasih.......................
