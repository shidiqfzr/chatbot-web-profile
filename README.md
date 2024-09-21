# Chatbot Web Profile
Cara menambah data baru ke rasa:
misalnya, jika user bertanya pertanyaan" berikut:
- apa persyaratan pembuatan SKCK?
- apa saja syarat membuat SKCK?
- bagaimana cara membuat SKCK?
- dokumen apa yang dibutuhkan untuk membuat SKCK?

Diharapkan jawabannya sebagai berikut:
Setelah Anda mendapatkan surat pengantar dari Kelurahan dan rekomendasi ke Kantor Kecamatan, sebelum mengurus SKCK ke Polsek atau Polres, silakan lengkapi persyaratan ini.
  **Bagi WNI (Warga Negara Indonesia):**
  - Fotokopi Kartu Tanda Penduduk (KTP) atau Surat Izin Mengemudi (SIM).
  - Fotokopi Kartu Keluarga (KK).
  - Fotokopi Akta Kelahiran/Surat Kenal Lahir/Ijazah Terakhir.
  - Pas foto 4x6 berlatar merah sebanyak 6 lembar.
  **Bagi WNA (Warga Negara Asing):**
  - Fotokopi Paspor.
  - Surat Sponsor dari Perusahaan (Asli).
  - Fotokopi Surat Nikah.
  - Fotokopi Kartu Izin Tinggal Terbatas (Kitas) atau Kartu Izin Tinggal Tetap (Kitap).
  - Pas foto 4x6 berlatar kuning sebanyak 6 lembar.

1. buka file data/nlu.yml.
Tambahkan intent baru, misalnya ask_skck_requirements, dengan beberapa contoh pertanyaan pengguna.
```yml
- intent: ask_skck_requirements
    examples: |
      - apa persyaratan pembuatan SKCK?
      - apa saja syarat membuat SKCK?
      - bagaimana cara membuat SKCK?
      - dokumen apa yang dibutuhkan untuk membuat SKCK?

2. Buka file domain.yml.
Tambahkan respons di bagian responses.
```yml
responses:
  utter_skck_requirements:
    - text: |
        Setelah Anda mendapatkan surat pengantar dari Kelurahan dan rekomendasi ke Kantor Kecamatan, sebelum mengurus SKCK ke Polsek atau Polres, silakan lengkapi persyaratan ini.

        **Bagi WNI (Warga Negara Indonesia):**
        - Fotokopi Kartu Tanda Penduduk (KTP) atau Surat Izin Mengemudi (SIM).
        - Fotokopi Kartu Keluarga (KK).
        - Fotokopi Akta Kelahiran/Surat Kenal Lahir/Ijazah Terakhir.
        - Pas foto 4x6 berlatar merah sebanyak 6 lembar.

        **Bagi WNA (Warga Negara Asing):**
        - Fotokopi Paspor.
        - Surat Sponsor dari Perusahaan (Asli).
        - Fotokopi Surat Nikah.
        - Fotokopi Kartu Izin Tinggal Terbatas (Kitas) atau Kartu Izin Tinggal Tetap (Kitap).
        - Pas foto 4x6 berlatar kuning sebanyak 6 lembar.

3. Buka file data/rules.yml. Tambahkan rule baru.
```yml
rules:
  - rule: Respond to ask_skck_requirements
    steps:
      - intent: ask_skck_requirements
      - action: utter_skck_requirements

4. train lagi modelnya:
```bash
rasa train

5. jalankan lagi chabotnya:
```bash
rasa shell

Silahkan coba tanyakan.
