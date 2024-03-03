class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def tambah_di_awal(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    def tambah_di_akhir(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last = self.head
        while last.next:
            last = last.next
        last.next = new_node

    def tambah_di_antara(self, posisi, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        temp = self.head
        for _ in range(posisi - 1):
            if temp.next is None:
                raise ValueError("Posisi melebihi panjang linked list")
            temp = temp.next
        new_node.next = temp.next
        temp.next = new_node

    def hapus_di_awal(self):
        if not self.head:
            print("Linked list sudah kosong")
            return
        self.head = self.head.next

    def hapus_di_akhir(self):
        if not self.head:
            print("Linked list sudah kosong")
            return
        if self.head.next is None:
            self.head = None
            return
        temp = self.head
        while temp.next.next:
            temp = temp.next
        temp.next = None

    def hapus_di_antara(self, posisi):
        if not self.head:
            print("Linked list sudah kosong")
            return
        temp = self.head
        if posisi == 0:
            self.head = temp.next
            temp = None
            return
        for _ in range(posisi - 1):
            if temp is None or temp.next is None:
                raise ValueError("Posisi melebihi panjang linked list")
            temp = temp.next
        if temp.next is None:
            raise ValueError("Posisi melebihi panjang linked list")
        next_node = temp.next.next
        temp.next = None
        temp.next = next_node

class Barang:
    def __init__(self, nama, jumlah, harga):
        self.nama = nama
        self.jumlah = jumlah
        self.harga = harga

    def __str__(self):
        return f"Nama: {self.nama}, Jumlah: {self.jumlah}, Harga: {self.harga}"

class ManajemenInventaris:
    def __init__(self):
        self.inventaris = {}

    def tambah_item_di_awal(self, jenis, item):
        if jenis not in self.inventaris:
            self.inventaris[jenis] = LinkedList()
        self.inventaris[jenis].tambah_di_awal(item)

    def tambah_item_di_akhir(self, jenis, item):
        if jenis not in self.inventaris:
            self.inventaris[jenis] = LinkedList()
        self.inventaris[jenis].tambah_di_akhir(item)

    def tambah_item_di_antara(self, jenis, posisi, item):
        if jenis not in self.inventaris:
            self.inventaris[jenis] = LinkedList()
        self.inventaris[jenis].tambah_di_antara(posisi, item)

    def hapus_item_di_awal(self, jenis):
        if jenis in self.inventaris:
            self.inventaris[jenis].hapus_di_awal()
        else:
            print("Inventaris untuk jenis", jenis, "kosong.")

    def hapus_item_di_akhir(self, jenis):
        if jenis in self.inventaris:
            self.inventaris[jenis].hapus_di_akhir()
        else:
            print("Inventaris untuk jenis", jenis, "kosong.")

    def hapus_item_di_antara(self, jenis, posisi):
        if jenis in self.inventaris:
            self.inventaris[jenis].hapus_di_antara(posisi)
        else:
            print("Inventaris untuk jenis", jenis, "kosong.")

    def tampilkan_inventaris(self, jenis):
        if jenis in self.inventaris:
            print(f"Inventaris {jenis} Saat Ini:")
            current_node = self.inventaris[jenis].head
            while current_node:
                print(current_node.data)
                current_node = current_node.next
        else:
            print("Inventaris untuk jenis", jenis, "kosong.")

    def perbarui_item(self, jenis, nama_item, jumlah_baru):
        if jenis in self.inventaris:
            temp = self.inventaris[jenis].head
            while temp:
                if temp.data.nama == nama_item:
                    temp.data.jumlah = jumlah_baru
                    print("Item berhasil diperbarui.")
                    return
                temp = temp.next
            print("Item tidak ditemukan dalam inventaris.")
        else:
            print("Inventaris untuk jenis", jenis, "kosong.")

    def hapus_item(self, jenis, nama_item):
        if jenis in self.inventaris:
            temp = self.inventaris[jenis].head
            prev = None
            while temp:
                if temp.data.nama == nama_item:
                    if prev:
                        prev.next = temp.next
                    else:
                        self.inventaris[jenis].head = temp.next
                    print("Item berhasil dihapus.")
                    return
                prev = temp
                temp = temp.next
            print("Item tidak ditemukan dalam inventaris.")
        else:
            print("Inventaris untuk jenis", jenis, "kosong.")

def main():
    manajemen_inventaris = ManajemenInventaris()

    while True:
        print("\nSistem Manajemen Inventaris")
        print("1. Tambah Barang")
        print("2. Tampilkan Inventaris")
        print("3. Perbarui Jumlah Item")
        print("4. Hapus Item")
        print("0. Keluar")

        pilihan = input("Masukkan pilihan Anda: ")

        if pilihan == '1':
            jenis = input("Masukkan jenis barang: ")
            nama = input("Masukkan nama barang: ")
            jumlah = int(input("Masukkan jumlah barang: "))
            harga = float(input("Masukkan harga barang: "))
            item = Barang(nama, jumlah, harga)
            posisi = input("Pilih posisi tambah (awal/antara/akhir): ").lower()
            if posisi == 'awal':
                manajemen_inventaris.tambah_item_di_awal(jenis, item)
            elif posisi == 'antara':
                posisi = int(input("Masukkan posisi tambah: "))
                manajemen_inventaris.tambah_item_di_antara(jenis, posisi, item)
            elif posisi == 'akhir':
                manajemen_inventaris.tambah_item_di_akhir(jenis, item)
            else:
                print("Posisi tidak valid.")

        elif pilihan == '2':
            jenis = input("Masukkan jenis barang untuk ditampilkan: ")
            manajemen_inventaris.tampilkan_inventaris(jenis)

        elif pilihan == '3':
            jenis = input("Masukkan jenis barang: ")
            nama = input("Masukkan nama item untuk memperbarui jumlah: ")
            jumlah_baru = int(input("Masukkan jumlah baru: "))
            manajemen_inventaris.perbarui_item(jenis, nama, jumlah_baru)

        elif pilihan == '4':
            jenis = input("Masukkan jenis barang: ")
            nama = input("Masukkan nama item untuk dihapus: ")
            manajemen_inventaris.hapus_item(jenis, nama)

        elif pilihan == '0':
            print("Keluar dari program.")
            break
        else:
            print("Pilihan tidak valid. Silakan masukkan opsi yang benar.")

if __name__ == "__main__":
    main()
