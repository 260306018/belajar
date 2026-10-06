# Modul 1 - Tabel Pengujian Logika (AND, OR, XOR)
# Mata Kuliah: Matematika Diskrit
 
def kondisi_and(a, b, c):
    return a and b and c
 
def kondisi_or(a, b, c):
    return a or b or c
 
def kondisi_xor(a, b):
    return a ^ b
 
 
# Kasus 4: pada tabel hanya baris "Pelajar saja" yang mendapat potongan
def kondisi_diskon(a, b, c):
    return a and not b and not c
 
 
def uji_kasus(nomor, judul, operator, kolom, fungsi,
              pesan_benar, pesan_salah, data):
    lebar = [max(len(k), 5) for k in kolom]
    print(f"Kasus {nomor}: {judul} ({operator})")
    print(" | ".join(f"{k:<{w}}" for k, w in zip(kolom, lebar)) + " | Hasil")
    for masukan in data:
        hasil = pesan_benar if fungsi(*masukan) else pesan_salah
        nilai = " | ".join(f"{str(m):<{w}}" for m, w in zip(masukan, lebar))
        print(f"{nilai} | {hasil}")
    print()
 
 
T, F = True, False
 
uji_kasus(
    1, "Beasiswa", "AND",
    ["Nilai Bagus", "Rajin", "Prasyarat"], kondisi_and,
    "Mendapat BEASISWA", "Tidak Mendapat BEASISWA",
    [(T, T, T),
     (T, F, T),
     (F, T, F),
     (F, F, T),
     (F, F, F)])
 
uji_kasus(
    2, "Aturan Kelulusan", "AND",
    ["Nilai Tinggi", "Aktif Organisasi", "Kartu Aktif"], kondisi_and,
    "Peserta LULUS", "Peserta Tidak LULUS",
    [(T, T, T),
     (T, F, T),
     (F, T, F),
     (F, F, T),
     (F, F, F)])
 
uji_kasus(
    3, "Pesta Kelulusan", "AND",
    ["Memiliki Kartu", "Memakai Jas", "Undangan"], kondisi_and,
    "Boleh Masuk Pesta", "Tidak Boleh Masuk Pesta",
    [(T, T, T),
     (F, F, T),
     (F, T, F),
     (F, F, T),
     (F, F, F)])
 
uji_kasus(
    4, "Diskon Buku di Toko", "OR",
    ["Pelajar", "Member", "Uang"], kondisi_diskon,
    "Mendapat potongan HARGA", "Tidak mendapat potongan HARGA",
    [(T, F, F),
     (F, T, F),
     (F, F, T),
     (T, T, F),
     (F, F, F)])
 
uji_kasus(
    5, "Pesta Pernikahan", "OR",
    ["Anggota", "Undangan", "Keluarga"], kondisi_or,
    "Boleh Mengikuti KEGIATAN", "Tidak Boleh Mengikuti KEGIATAN",
    [(T, F, F),
     (F, T, F),
     (F, F, T),
     (T, T, F),
     (F, F, F)])
 
uji_kasus(
    6, "Melamar Pekerjaan", "OR",
    ["Prestasi", "Sertifikat", "Kemampuan"], kondisi_or,
    "Mendapat Pekerjaan", "Tidak Mendapat Pekerjaan",
    [(T, F, F),
     (F, T, F),
     (F, F, T),
     (T, T, F),
     (F, F, F)])
 
uji_kasus(
    7, "Lampu Lalu Lintas", "XOR",
    ["Lampu Hijau", "Lampu Merah"], kondisi_xor,
    "VALID", "Tidak VALID",
    [(T, F),
     (F, T),
     (T, T),
     (F, F)])
 
uji_kasus(
    8, "Cara Login Akun", "XOR",
    ["Sandi Benar", "OTP Benar"], kondisi_xor,
    "LOGIN BERHASIL", "LOGIN GAGAL",
    [(T, F),
     (F, T),
     (T, T),
     (F, F)])
 
