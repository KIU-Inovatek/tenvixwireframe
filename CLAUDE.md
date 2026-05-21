# TENVIX Wireframe v7.2 — CLAUDE.md

> File ini dibaca otomatis oleh Claude Code setiap sesi dimulai.
> Tidak perlu paste ulang. Langsung ketik: `Build the wireframe`

---

## TUJUAN

Buatkan satu file HTML interaktif bernama `tenvix-wireframe-v72.html` untuk wireframe/prototype TENVIX — platform tender LPSE Indonesia.

File ini harus bisa dibuka langsung di browser tanpa server, tanpa install apapun. Semua state disimpan di localStorage.

---

## KONTEKS PRODUK

TENVIX adalah platform tender Indonesia dengan dua sisi user yang sepenuhnya terpisah:
- **Demand side** — kontraktor yang mencari tender (tenvix.id)
- **Supply side** — Tenaga Ahli, Vendor SBU, Notaris KSO, Supplier material (tenvix.id/mitra)

TENVI adalah fitur chat di platform — bukan AI, bukan LLM. TENVI adalah **keyword-based search engine** yang parsing input user → query database → return hasil dalam bubble chat. Semua respons TENVI dibuat dari template kalimat + hasil matching keyword.

---

## STYLING & DESAIN

### Color Palette — Diambil langsung dari logo TENVIX

```css
:root {
  /* === PRIMARY BRAND === */
  --blue-bright:   #0076FF;   /* biru terang — ikon T bagian kiri */
  --blue-mid:      #0099FF;   /* biru tengah — gradient ikon T */
  --cyan-light:    #00D4FF;   /* cyan terang — gradient ikon T kanan */
  --cyan-vivid:    #00E7FB;   /* cyan vivid — ujung ikon T */
  --navy-deep:     #091232;   /* navy sangat gelap — wordmark TENVIX */
  --navy-mid:      #0A1538;   /* navy — body teks utama */
  --cyan-accent:   #10E1FF;   /* cyan accent — huruf X di logo */

  /* === BACKGROUNDS === */
  --bg-white:      #FFFFFF;
  --bg-light:      #F4F6FB;   /* off-white kebiruan untuk surface */
  --bg-surface:    #EDF2F9;   /* surface card */
  --bg-navy:       #091232;   /* background gelap supply/internal */
  --bg-navy-card:  #0D1840;   /* card di atas navy */
  --bg-navy-hover: #111E4A;   /* hover state di navy */

  /* === TEKS === */
  --text-navy:     #091232;   /* teks utama di background putih */
  --text-body:     #2A3550;   /* teks body — navy lebih terang */
  --text-muted:    #566177;   /* teks sekunder */
  --text-hint:     #8A94A8;   /* placeholder, hint */
  --text-white:    #FFFFFF;   /* teks di background gelap */
  --text-white-70: rgba(255,255,255,0.7); /* teks muted di bg gelap */

  /* === ACCENT & STATUS === */
  --accent-cyan:   #00D4FF;   /* primary action di bg gelap */
  --accent-blue:   #0076FF;   /* primary action di bg terang */
  --success:       #00B87A;   /* hijau sukses */
  --warning:       #F5A623;   /* kuning warning */
  --danger:        #E53935;   /* merah error/hapus */
  --internal-red:  #C62828;   /* accent halaman internal */

  /* === BORDER === */
  --border-light:  #D8E2F0;   /* border di bg putih */
  --border-mid:    #B0C0D8;   /* border lebih tegas */
  --border-navy:   #1A2855;   /* border di bg navy */
  --border-cyan:   #00D4FF;   /* border active/focus di bg gelap */
}
```

### Demand Side (tenvix.id)
- **Background halaman**: `--bg-light` (#F4F6FB)
- **Nav/header**: `--navy-deep` (#091232) dengan logo putih + teks nav putih
- **Sidebar**: putih (#fff) dengan border kanan `--border-light`, active item: background `--bg-surface`, border kiri 3px `--accent-blue`
- **Card**: background putih, border 1px `--border-light`, border-radius 6px, shadow ringan
- **Teks utama**: `--text-navy` (#091232)
- **Teks sekunder**: `--text-muted` (#566177)
- **Tombol primary**: background `--accent-blue` (#0076FF), teks putih, hover darken 10%
- **Tombol outline**: border `--accent-blue`, teks `--accent-blue`, hover: bg `--bg-surface`
- **Tombol danger**: border `--danger`, teks `--danger`
- **Badge LPSE**: background #E8F0FF, teks #0076FF, border #B8D0FF
- **Badge BUMN**: background #FFF3E0, teks #E65100, border #FFB74D
- **Badge Swasta**: background #E8F5E9, teks #2E7D32, border #A5D6A7
- **SBU Match hijau**: background #E3F8F0, teks #00875A, border #00B87A
- **SBU Match kuning (partial)**: background #FFF8E1, teks #F57F17, border #F5A623
- **Stat card**: background `--bg-surface` (#EDF2F9), number besar `--navy-deep`, label `--text-muted`
- **TENVI chatbox**: background `--navy-deep`, header lebih gelap, bubble teks putih
- **Bubble user**: background `--accent-blue` (#0076FF), teks putih
- **Bubble TENVI**: background `--bg-navy-card` (#0D1840), teks putih, border `--border-navy`

### Supply Side (tenvix.id/mitra)
- **Background halaman**: `--bg-navy` (#091232)
- **Nav/header**: navy lebih gelap (#060D20) dengan border bawah `--cyan-accent` (#10E1FF)
- **Logo di nav**: "TENVIX MITRA" dengan wordmark putih + "MITRA" cyan
- **Sidebar**: background #0D1840, border kanan `--border-navy`, active item border kiri 3px `--accent-cyan`
- **Card**: background `--bg-navy-card` (#0D1840), border 1px `--border-navy`, border-radius 6px
- **Teks utama**: `--text-white` (#FFFFFF)
- **Teks sekunder**: `--text-white-70`
- **Heading section**: `--cyan-accent` (#10E1FF)
- **Tombol primary**: background `--cyan-accent` (#10E1FF), teks `--navy-deep`, font-weight 700
- **Tombol outline**: border `--border-navy`, teks `--text-white-70`, hover border `--cyan-accent`
- **Badge aktif**: background #0A2040, teks #00D4FF, border #00D4FF
- **Badge expired/error**: background #3A0A0A, teks #FF6B6B, border #E53935
- **Badge warning**: background #2A1A00, teks #F5A623, border #F5A623
- **Stat card number**: `--cyan-accent` (#10E1FF)
- **Input field**: background #060D20, border `--border-navy`, teks putih, focus border `--cyan-accent`
- **Kredit WA box**: background #091232, border 2px `--cyan-accent`, teks cyan
- **Progress bar fill**: gradient dari `--blue-mid` ke `--cyan-accent`

### Internal (CMS BUMN + Dashboard Direktur)
- **Sama dengan supply side** tapi:
- **Accent**: `--internal-red` (#C62828) menggantikan cyan
- **Nav border bawah**: `--internal-red`
- **Heading section**: `--internal-red`
- **Tombol primary**: background `--internal-red`
- **Stat card number**: `--internal-red`
- **Sidebar active border**: `--internal-red`

### Logo SVG (buat di setiap nav)
Buat logo SVG sederhana yang merepresentasikan:
- Ikon "T" geometric dengan gradient biru (#0076FF) → cyan (#00D4FF) dari kiri ke kanan
- Wordmark "TENVIX" dalam font bold sans-serif, warna `--navy-deep` di bg terang / putih di bg gelap
- Huruf "X" di wordmark dalam warna `--cyan-accent` (#10E1FF)
- Tagline "the ai platform built to win tenders" di bawah (hanya di landing, font kecil, warna muted)

Contoh SVG logo minimal untuk nav:
```html
<svg width="120" height="32" viewBox="0 0 120 32">
  <!-- Ikon T geometric -->
  <defs>
    <linearGradient id="tGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" style="stop-color:#0076FF"/>
      <stop offset="100%" style="stop-color:#00D4FF"/>
    </linearGradient>
  </defs>
  <polygon points="2,2 18,2 18,8 12,8 12,30 8,30 8,8 2,8" fill="url(#tGrad)"/>
  <!-- Wordmark TENVIX -->
  <text x="24" y="22" font-family="Arial" font-weight="900" font-size="16" fill="currentColor">TENVI</text>
  <text x="92" y="22" font-family="Arial" font-weight="900" font-size="16" fill="#10E1FF">X</text>
</svg>
```
Sesuaikan `currentColor` dengan konteks (putih di bg gelap, navy di bg terang).

### Typography
- Font: Arial, sans-serif (konsisten dengan wireframe sebelumnya)
- Heading utama: font-weight 900, `--text-navy` / putih
- Subheading section: font-weight 700, 11px uppercase letter-spacing 0.5px
- Body: font-weight 400, 12-13px
- Tombol: font-weight 700, 10-11px

### Komponen Visual Tambahan
- **Border-radius**: card 6px, tombol 4px, badge 3px, input 4px
- **Box shadow card demand**: `0 1px 4px rgba(9,18,50,0.08)`
- **Transition**: semua hover state `transition: 0.15s ease`
- **Focus ring input**: `box-shadow: 0 0 0 3px rgba(0,118,255,0.2)`
- **Gradient header demand** (opsional): linear-gradient dari `--navy-deep` ke `#0A1A4A`

---

## ARSITEKTUR FILE

Single HTML file dengan:
- CSS di `<style>` tag
- Semua JavaScript inline di `<script>` tag
- Tidak ada CDN eksternal, tidak ada framework
- localStorage untuk semua state (user session, form data, favorit, dll)

---

## DATA DUMMY

### 30 Tender Dummy
Buat array `TENDERS` berisi 30 objek dengan field:
```
kode_tender, nama, instansi, nilai_pagu, hps, deadline, metode,
sumber (LPSE/BUMN/Swasta), kategori, wilayah, required_sbu (array),
kualifikasi_min, status (terbuka/tutup)
```

Variasi yang harus ada:
- Sumber: 20 LPSE, 7 BUMN (PT Pertamina, PT PLN, PT Wijaya Karya, PT Pelindo, PT Jasa Marga, PT KAI, PT Angkasa Pura), 3 Swasta
- Kategori: Konstruksi Jalan, Bangunan Gedung, Jembatan, Drainase, Mekanikal Elektrikal, Pengadaan Material, IT/Sistem
- Wilayah: DKI Jakarta, Jawa Barat, Jawa Tengah, Jawa Timur, Banten, Sumatera Utara, Kalimantan Timur, Sulawesi Selatan
- Nilai pagu: bervariasi dari Rp 300jt sampai Rp 45M
- SBU: campuran BS001, BS002, BS003, BS007, BS008, BS009, ME001, ME003, EL001, SI001
- Deadline: bervariasi 3 hari sampai 45 hari dari hari ini

### 15 SBU Onboarding
```javascript
const SBU_LIST = [
  { kode: 'BS001', nama: 'Bangunan Gedung', sub: 'Sipil' },
  { kode: 'BS002', nama: 'Bangunan Gedung Bertingkat', sub: 'Sipil' },
  { kode: 'BS003', nama: 'Bangunan Pabrik & Gudang', sub: 'Sipil' },
  { kode: 'BS007', nama: 'Jalan Raya', sub: 'Sipil' },
  { kode: 'BS008', nama: 'Jalan Tol', sub: 'Sipil' },
  { kode: 'BS009', nama: 'Jembatan', sub: 'Sipil' },
  { kode: 'BS010', nama: 'Drainase & Irigasi', sub: 'Sipil' },
  { kode: 'BS011', nama: 'Bangunan Pelabuhan', sub: 'Sipil' },
  { kode: 'BS013', nama: 'Pekerjaan Fondasi', sub: 'Sipil' },
  { kode: 'ME001', nama: 'Instalasi Mekanikal', sub: 'Mekanikal' },
  { kode: 'ME003', nama: 'Instalasi HVAC', sub: 'Mekanikal' },
  { kode: 'ME005', nama: 'Instalasi Pipa (Plumbing)', sub: 'Mekanikal' },
  { kode: 'EL001', nama: 'Instalasi Elektrikal', sub: 'Elektrikal' },
  { kode: 'EL003', nama: 'Instalasi Sistem Keamanan', sub: 'Elektrikal' },
  { kode: 'SI001', nama: 'Sistem Informasi & IT', sub: 'Teknologi' },
];
```

### Data Supply Dummy
Buat array untuk masing-masing role:
- 8 Tenaga Ahli (nama, SKK, jenjang, rate, wilayah, rating, ulasan)
- 6 Vendor SBU (nama perusahaan, SBU, kualifikasi, area, rating)
- 4 Notaris (nama, wilayah, estimasi biaya, rating)
- 5 Supplier (nama, produk utama, area, rating)

---

## STRUKTUR HALAMAN

### DEMAND SIDE (11 halaman)

**P0 — Landing**
- Hero: tagline "Menang Tender Dimulai dari Satu Pertanyaan"
- TENVI chatbox di tengah (fungsional, bisa ketik dan dapat respons)
- Di bawah chatbox: contoh preset query (tombol klik langsung kirim ke TENVI)
- Link kecil di pojok bawah: "Daftar sebagai Mitra Supply →"
- Nav: tombol "Masuk" dan "Daftar"
- State unregistered: TENVI bisa dipakai tapi hasil dibatasi 3 saja + prompt login

**P1 — Login / Register**
- Satu form dengan tab: "Masuk" | "Daftar"
- Form masuk: email + password + tombol Masuk
- Form daftar: nama perusahaan + email + password + no HP
- Link "Lupa password?" di bawah form masuk
- Setelah login: sistem cek localStorage → kalau akun demand → onboarding/dashboard demand, kalau akun supply → onboarding/dashboard supply
- Setelah register demand: → Onboarding P1a
- Setelah register supply: → P1b (pilih role supply dulu)
- Error state: email tidak terdaftar, password salah, email sudah dipakai

**P1a — Forgot Password**
- Step 1: input email → tombol "Kirim Link Reset"
- Step 2: pesan konfirmasi "Email reset dikirim ke [email]" + simulasi link "Klik di sini untuk reset (simulasi)"
- Step 3: form buat password baru (password + konfirmasi password)
- Step 4: sukses → redirect ke login

**P1b — Register Supply — Pilih Role**
- Halaman pilih role: 4 card besar (TA / Vendor SBU / Notaris / Supplier)
- Tiap card: icon, nama role, deskripsi singkat 1 baris
- Setelah pilih: → Onboarding Supply per role (P1c)

**P1c — Onboarding Supply (per role)**
- Progress bar 2 step di atas
- Step 1: form data dasar per role
  - TA: nama lengkap, no KTP, email, WA, domisili, klasifikasi SKK, jenjang (Muda/Madya/Utama), berlaku s/d, rate, wilayah kerja, status tersedia
  - Vendor: nama perusahaan, NIB, NPWP, email, WA, kode SBU (multi-select dari list), kualifikasi, area layanan
  - Notaris: nama, no SK, email, WA, wilayah kerja (sesuai SK), estimasi biaya, layanan KSO (ya/tidak)
  - Supplier: nama perusahaan, NIB, email, WA, area pengiriman, min order, 3 produk utama (nama + satuan + harga)
- Step 2: preview profil + konfirmasi
- Setelah submit → Dashboard supply per role (dengan data yang baru diisi)

**P2 — Onboarding Demand (3 step)**
- Progress bar 3 step di atas: "Profil" → "SBU" → "Kualifikasi"
- Step 1 — Profil perusahaan:
  - Nama perusahaan, NIB, NPWP, no WA, domisili (kota + provinsi)
  - Validasi: semua field wajib diisi sebelum bisa next
- Step 2 — Pilih SBU yang dimiliki:
  - Grid checklist dari 15 SBU_LIST di atas
  - Grouped by sub-kategori (Sipil / Mekanikal / Elektrikal / Teknologi)
  - Bisa pilih multiple, minimal 1 harus dipilih
  - Di bawah: "Belum punya SBU? Lanjut dulu, bisa diisi nanti"
- Step 3 — Kualifikasi & konfirmasi:
  - Pilih kualifikasi: Kecil / Menengah / Besar (radio button)
  - Ringkasan: nama perusahaan, SBU dipilih, kualifikasi
  - Tombol "Mulai Gunakan TENVIX"
- Setelah submit → Dashboard (empty state)

**P3 — Dashboard Demand**
- Upsell banner Business (jika paket Basic/Free)
- 4 stat card: Tender Aktif / Favorit / Notif Baru / Vault %
- Empty state (jika baru onboarding): ilustrasi + teks + tombol CTA
- Jika sudah ada data: tabel tender terbaru + TENVI quick ask
- Vault progress bar

**P4 — Cari Tender (TENVI)**
- TENVI chatbox full width
- Fungsional: user ketik keyword → TENVI parse → tampilkan hasil dalam bubble chat sebagai tabel
- Keyword yang dikenali: nama bidang, kode SBU, wilayah, nilai pagu (format: "max 5M", "di atas 1M"), deadline ("minggu ini", "bulan ini"), sumber ("BUMN", "LPSE"), kualifikasi
- Tabel hasil: Kode Tender | Nama | Instansi | Pagu | Deadline | Sumber | SBU Match | Aksi
- SBU Match badge: hijau "✓ Match" jika semua SBU user ada di required_sbu tender, kuning "~ Partial" jika sebagian, abu "– Tidak cocok" jika tidak ada. Hover badge → tooltip detail SBU apa yang kurang
- Kolom Aksi: "Salin Kode" untuk LPSE, "Buka ↗" untuk BUMN/Swasta
- Salin Kode: tombol berubah "✓ Disalin!" hijau 2 detik setelah klik
- Pagination: tampilkan 10 per halaman, ada navigasi « 1 2 3 ... » di bawah tabel
- Error state: kalau 0 hasil → bubble TENVI saran keyword lain
- Preset query di bawah input: "Tender baru hari ini" | "Deadline minggu ini" | "Sesuai SBU saya" | "BUMN terbaru"

**P5 — Detail Tender**
- Info tender lengkap (semua field dari data dummy)
- Kode tender + tombol "Salin Kode" (dengan feedback 2 detik)
- SBU Match analysis: tabel Vault user vs Syarat tender (centang hijau / silang merah per item)
- Tombol "Buka ↗" hanya tampil untuk BUMN/Swasta
- AI Classification box (label PRO+): kalau user Basic/Free → klik → modal upsell muncul. Kalau Pro → tampil konten analisa (persaingan, kompleksitas, rekomendasi)
- Tombol "Simpan ke Favorit" / "Hapus dari Favorit" (toggle)

**P6 — Vault Dokumen**
- Progress bar kelengkapan (% dari total item yang dicentang)
- 4 kategori: Legalitas / Sertifikasi SBU & SKK / Keuangan / Pengalaman & SDM
- Setiap item: checkbox yang bisa diklik (toggle centang/hapus centang)
- Simpan otomatis ke localStorage setiap centang berubah
- Toast "Vault diperbarui" muncul 2 detik setelah perubahan
- Catatan: "Vault hanya menyimpan status centang. Tidak ada upload dokumen."

**P7 — Ekosistem**
- TENVI chatbox untuk cari supply
- Keyword yang dikenali: "cari TA", "butuh vendor", "notaris KSO", "supplier beton" dll
- Hasil dalam bubble: card per supply dengan nama, spesifikasi, rating (jika ≥3 ulasan), tombol "Hubungi via Chat →"
- 4 category card di bawah: Tenaga Ahli / Vendor SBU / Notaris / Supplier
- Klik category → TENVI langsung filter dan tampilkan semua supply di kategori itu

**P8 — Favorit**
- Daftar tender tersimpan
- Sort: Deadline Terdekat / Nilai Terbesar / SBU Match
- Empty state jika kosong
- Hapus favorit: tombol Hapus → inline konfirmasi "Yakin hapus? [Ya] [Batal]" → kalau Ya: hilang dengan animasi fade

**P9 — Notifikasi**
- Manajemen keyword: tag input, tambah/hapus keyword
- Filter: pagu / sumber / SBU match
- Toggle channel: WhatsApp / Email / Push Browser
- Riwayat notifikasi: dot merah = belum baca, dot abu = sudah baca

**P10 — Inbox Chat**
- List percakapan di kiri (dengan supply dari Ekosistem)
- Chat thread di kanan
- @TENVI bisa di-tag dalam thread → TENVI jawab inline dengan label "↩ @TENVI:"
- Empty state kalau belum ada percakapan

**P11 — Akun & Paket**
- Profil perusahaan (form edit, data dari onboarding)
- Paket aktif dengan detail fitur
- Tabel 4 tier: Free / Basic Rp 99rb / Pro Rp 299rb / Business Rp 799rb
- Tombol upgrade → untuk Pro+ jika sudah Pro, tampil fitur. Untuk tier lebih tinggi → modal konfirmasi + simulasi sukses
- Vault progress
- Tombol Logout (merah, di bawah sendiri): klik → inline konfirmasi "Yakin keluar?" → [Ya, Keluar] [Batal] → kalau Ya: clear localStorage → redirect ke landing

---

### SUPPLY SIDE (halaman S)

**S0 — Login Mitra**
- URL: tenvix.id/mitra (simulasikan dengan section terpisah)
- Form login: email + password
- Link "Daftar sebagai Mitra" → ke P1b (pilih role)
- Catatan kecil: "Akun mitra terpisah dari akun kontraktor"
- Setelah login → identify role dari localStorage → masuk dashboard role yang sesuai

**S1–S4 — Dashboard per Role (TA / Vendor / Notaris / Supplier)**
Masing-masing dashboard berbeda, tapi struktur sama:
- 4 stat card (berbeda per role)
- Inbox permintaan masuk (dari demand via Ekosistem)
  - Kalau **belum subscribe WA**: pesan baris pertama terbaca, sisanya blur dengan overlay "Subscribe untuk membaca & membalas →". Tombol Balas disabled dengan tooltip "Aktifkan subscription dulu"
  - Kalau **sudah subscribe**: pesan full terbaca, tombol Balas aktif
- Kelengkapan profil (progress bar)
- Subscription WA status (TA: Rp 129rb/bln, Vendor: Rp 199rb/bln, Notaris: Rp 199rb/bln, Supplier: kredit prepaid Rp 500/notif)
- Toggle ketersediaan (Notaris & TA): klik langsung berubah + toast "Status diperbarui" 2 detik
- Supplier: tampilkan saldo kredit WA + tombol isi saldo

**S5–S8 — Edit Profil per Role**
- Form edit semua field yang diisi saat onboarding
- Tombol Simpan → toast sukses
- Tampilkan ulasan (min 3 untuk tampil bintang publik)
- Catatan: "TENVI memediasi semua ulasan. Tidak bisa diblock."

**S9 — Inbox Chat Supply**
- Sama dengan P10 demand tapi dari sisi supply
- Pesan dari kontraktor muncul di sini
- Kalau belum subscribe: baris pertama terbaca, sisanya blur + overlay subscribe
- @TENVI bisa di-tag
- Thread gelap (background #080808)

---

### INTERNAL (2 halaman)

**I1 — CMS BUMN**
- Khusus admin TENVIX
- Tabel status sumber BUMN (nama, status aktif/error, terakhir update, tombol aksi)
- Checklist verifikasi
- Form input tender manual (sumber: URL/Screenshot/PDF, instansi, kategori, prioritas)
- Laporan hari ini (LPSE / BUMN / Manual / Error)

**I2 — Dashboard Direktur**
- Revenue & konversi per paket (tabel)
- Platform activity (pencarian/hari, chat TENVI, uptime, response avg)
- Ekosistem supply (jumlah aktif per role, kontak/hari, konversi)
- WA & chat activity (notif/hari, revenue WA/hari, delivery rate)

---

## FLOW INTERAKTIF LENGKAP

### Flow Register Demand
1. Landing → klik "Daftar" → form register → submit → Onboarding Step 1
2. Onboarding: isi profil → next → pilih SBU → next → pilih kualifikasi → submit
3. Masuk Dashboard dengan empty state + welcome message

### Flow Login
1. Form login → submit → cek localStorage (akun demand atau supply)
2. Akun demand → dashboard demand
3. Akun supply → dashboard supply role yang sesuai
4. Email tidak dikenal → error "Email tidak terdaftar. Daftar dulu?"
5. Password salah → error "Password salah. Coba lagi atau reset password."

### Flow Forgot Password
1. Klik "Lupa password?" → halaman forgot password
2. Input email → submit → step konfirmasi "Email dikirim ke [email]"
3. Klik link simulasi → form password baru
4. Submit → sukses → redirect ke login

### Flow Register Supply
1. Landing → "Daftar sebagai Mitra" → halaman pilih role
2. Pilih role (TA/Vendor/Notaris/Supplier) → form onboarding step 1
3. Isi data → next → preview → submit → dashboard supply (empty state)

### Flow TENVI Search
1. User ketik di chatbox → parse keyword → query array TENDERS
2. Tampilkan dalam bubble chat sebagai tabel dengan pagination
3. Kalau 0 hasil → bubble saran keyword
4. User bisa klik preset query → langsung trigger search

### Flow Upsell Gate
1. User Free/Basic klik fitur Pro+ (AI Classification, Analisa Peluang lanjut, dll)
2. Modal overlay muncul: nama fitur + manfaat + perbandingan tier singkat
3. Tombol "Upgrade ke Pro" → simulasi checkout (konfirmasi → sukses → paket berubah)
4. Tombol "Nanti saja" → tutup modal

### Flow Logout
1. Klik Logout di halaman Akun
2. Inline konfirmasi: "Yakin keluar?" [Ya, Keluar] [Batal]
3. Klik Ya → clear semua localStorage → redirect ke landing (state unregistered)

---

## KOMPONEN UI YANG HARUS FUNGSIONAL

1. **Toast notification**: muncul di pojok kanan bawah, auto-hilang 2 detik. Warna: hijau (sukses), merah (error), kuning (warning)
2. **Modal overlay**: backdrop gelap semi-transparan, card di tengah, bisa tutup dengan klik backdrop atau tombol ×
3. **Salin Kode feedback**: tombol → "✓ Disalin!" hijau 2 detik → kembali normal
4. **SBU Match badge + tooltip**: hover → tooltip muncul di atas badge
5. **Pagination**: navigasi « prev | 1 | 2 | 3 | ... | next » di bawah tabel
6. **Toggle ketersediaan**: klik langsung berubah state + toast
7. **Inbox blur**: baris pertama terbaca, sisanya CSS blur + overlay
8. **Empty state**: pesan kontekstual per halaman (bukan layar kosong)
9. **Konfirmasi hapus inline**: tombol Hapus → ["Yakin hapus?"] [Ya] [Batal]
10. **Validasi form real-time**: border merah + pesan error di bawah field kalau kosong/format salah saat submit
11. **Progress bar onboarding**: menunjukkan step saat ini dari total step
12. **TENVI typing indicator**: "TENVI sedang mencari..." selama 1 detik sebelum hasil muncul

---

## LOCALSTORAGE SCHEMA

```javascript
// Key: 'tenvix_session'
{
  isLoggedIn: true,
  accountType: 'demand', // atau 'supply'
  supplyRole: null, // 'ta' | 'vendor' | 'notaris' | 'supplier'
  onboardingComplete: true,
  currentPlan: 'basic', // 'free' | 'basic' | 'pro' | 'business'
  waSubscribed: false // untuk supply
}

// Key: 'tenvix_demand_profile'
{
  namaPerusahaan: '',
  nib: '',
  npwp: '',
  wa: '',
  domisili: '',
  sbu: [], // array kode SBU
  kualifikasi: 'kecil' // 'kecil' | 'menengah' | 'besar'
}

// Key: 'tenvix_supply_profile'
{
  role: '',
  // field sesuai role
}

// Key: 'tenvix_vault'
{
  // kode_item: true/false
}

// Key: 'tenvix_favorites'
[] // array kode_tender

// Key: 'tenvix_accounts'
[] // array semua akun yang pernah register (untuk simulasi login)
```

---

## CATATAN PENTING UNTUK DEVELOPER

1. File harus bisa dibuka langsung di browser dengan `file://` tanpa server
2. Tidak boleh ada fetch/XHR ke URL eksternal
3. Semua navigasi antar halaman dengan show/hide div, bukan URL routing
4. Gunakan `window.history.pushState` untuk update URL bar (opsional tapi bagus untuk UX)
5. Tombol browser back harus berfungsi minimal untuk kembali ke halaman sebelumnya
6. Supply side dan demand side harus terasa seperti dua environment yang benar-benar berbeda (warna, atmosfer, menu)
7. Internal page (I1, I2) hanya bisa diakses jika login sebagai admin (buat akun admin dummy: admin@tenvix.id / password: admin123)
8. Semua data dummy harus cukup realistis — nama proyek, instansi, dan nilai pagu harus terasa seperti data tender Indonesia sungguhan
9. Jangan generate file dulu sebelum review struktur ini dengan user

---

## URUTAN BUILD YANG DISARANKAN

1. Setup struktur dasar HTML, CSS variables, font, warna per environment
2. Data dummy: TENDERS array (30), SBU_LIST (15), supply data
3. localStorage helper functions (get, set, clear)
4. Komponen UI reusable: toast, modal, badge, pagination
5. Flow auth: landing → register → onboarding demand → dashboard
6. Halaman demand satu per satu (P3 → P4 → P5 → P6 → P7 → P8 → P9 → P10 → P11)
7. TENVI search engine (keyword parser + query TENDERS)
8. Flow supply: register → pilih role → onboarding → dashboard
9. Halaman supply per role
10. Internal halaman (I1, I2)
11. Polish: empty states, error states, upsell gate, semua feedback visual
12. Test semua flow dari awal sampai akhir

---

*Prompt ini dibuat untuk TENVIX Wireframe v7.2 — scope final yang sudah disetujui.*
*Jangan mulai generate sebelum membaca dan memahami seluruh dokumen ini.*

---

## CARA PAKAI FILE INI

### Setup awal (sekali saja)
```bash
mkdir tenvix-wireframe
cd tenvix-wireframe
# Taruh CLAUDE.md di folder ini
claude  # buka Claude Code
```

### Setiap sesi
Claude Code otomatis baca CLAUDE.md ini. Cukup ketik:
```
Build the wireframe
```

### Kalau mau iterasi setelah file jadi
```
Update halaman P4 - tambahkan filter dropdown di atas TENVI chatbox
```
```
Fix bug: tombol Salin Kode tidak berubah jadi "✓ Disalin!"
```
```
Tambahkan animasi fade-in saat halaman berganti
```

### Output yang diharapkan
- File: `tenvix-wireframe-v72.html` di folder yang sama
- Buka di browser: double-click file atau `open tenvix-wireframe-v72.html`
- Tidak perlu server, tidak perlu npm install

---

*TENVIX Wireframe v7.2 — scope final yang sudah disetujui*
*Jangan generate sebelum membaca seluruh file ini*
