# Geri Yayılım Algoritmasının Adım Adım Türetimi

Hesaplamalı çizge ile görselleştirme ve UCI Wine Quality uygulaması

Prof. Dr. Hakan Çetinel · Yiğit Apaydın (210301124)  
Manisa Celal Bayar Üniversitesi, Makine Mühendisliği Bölümü

| İçerik | Dosya |
|---|---|
| Akademik bölüm | [PDF](Geri_Yayilim.pdf) · [Word](Geri_Yayilim.docx) |
| Kaynakça | [BibTeX](references.bib) |
| Kod, veri, notebook, modeller ve kayıtlı sonuçlar | [Proje ZIP’i](Geri_Yayilim_Projesi.zip) |
| Ayrı şekiller | [300 dpi PNG klasörü](Sekiller_300dpi/) |
| Veri kaynağı ve kullanım koşulları | [Veri lisansı](DATA_LICENSE.md) |
| Dosya bütünlüğü | [SHA-256 listesi](SHA256SUMS.txt) |

ZIP’i boş bir klasöre çıkarın. Kurulum ve çalıştırma adımları içindeki README’dedir; Python 3.12 kullanılır. `scripts/demo_backprop.py` küçük ağın hesabını, `scripts/verify_results.py` kayıtlı sonuçların ortalama ve standart sapmasını denetler. `scripts/run_notebook.py` açıklamalı not defterini çalıştırır. Bu inceleme komutları yeni Wine modeli eğitmez veya test kümesinde yeni tahmin üretmez.

ZIP içindeki `paper/` Word/PDF ve kaynakça, bu klasördeki belgelerin kopyalarıdır. `results/` özgün sayısal kayıtları, `models/` ana MLP’nin üç tohumla elde edilen parametrelerini içerir. Şekiller PNG/PDF biçiminde verilmiştir.

Eğitim, doğrulama ve test aşamalarının kapsamı akademik bölüm ile ZIP içindeki `docs/METHODS.md` dosyasında açıklanır.

