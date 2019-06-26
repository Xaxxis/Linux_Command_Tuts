# Linux Mapping Folder Command
Tutuorial ini adalah untuk mapping otomatis folder mapping dari nas dengan protokol CIFS:

Sebelum melakukan konfigurasi atau jika kondisi pc masih dalam keadaan fresh, install beberapa software dibawah ini:
- OpenSSH
- samba-client
dengan perintah:
    >sudo apt-get -y install cifs-utils openssh-server

Mounting File dari NAS Server
1. Buat file untuk username dan password nas di direktori /home/ubuntu dengan cara:
	- >sudo nano /home/ubuntu/.smbcredentials
	- isi dengan data:
		>username=namausernas
		>password=passwordusernas
	- tekan tombol 
      >ctrl + x
	- tekan Y, lalu enter

2. beri hak akses pada file .smbcredentials yang telah dibuat
	- >sudo chmod +x /home/ubuntu/.smbcredentials

3. Buat folder untuk mapping data yang akan di map dari NAS
	- >sudo mkdir /home/ubuntu/NAMA_FOLDER 
	-(NAMA_FOLDER, biasanya nama user)

4. Tambahkan baris dibawah ini agar, folder mapping otomatis saat booting.
	- buka file fstab dengan cara: 
      >sudo nano /etc/fstab
	- masukan baris dibawah ini pada file fstab. dan sesuaikan ip nas dan nama folder
		>//IP_NAS_SERVER/Kalimantan/Pomalaa/Stage1/ /home/ubuntu/NAMA_FOLDER cifs credentials=/home/ubuntu/.smbcredentials,dir_mode=0777,file_mode=0777,iocharset=utf8,nobrl 0 0
    - IP_NAS_SERVER = ip alamat server
    - NAMA_FOLDER = nama folder yang telah dibuat pada langkah ke 3

5. Test hasil konfigurasi dengan cara
    - > mount -a
