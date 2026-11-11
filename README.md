# Geri Yayılım Algoritmasının Adım Adım Türetimi

**Hesaplamalı çizge ile görselleştirme ve UCI Wine Quality uygulaması**

Prof. Dr. Hakan Çetinel · Yiğit Apaydın (210301124)  
Manisa Celal Bayar Üniversitesi, Makine Mühendisliği Bölümü

Bu çalışma, geri yayılımı dokuz parametreli küçük bir ağ üzerinde adım adım türetir. Türevler NumPy, PyTorch ve merkezî sonlu farkla karşılaştırılır. Gerçek veri uygulamasında kırmızı şarabın kalite puanı 11 ölçümden tahmin edilir.

## Teslim dosyaları

| İçerik | Dosya |
|---|---|
| Akademik bölüm | [PDF](Geri_Yayilim.pdf) · [Word](Geri_Yayilim.docx) |
| 35 kaynaklı kaynakça | [BibTeX](references.bib) |
| Kod, veri, notebook, testler, şekiller, kayıtlı modeller ve sonuçlar | [Tam proje ZIP’i](Geri_Yayilim_Projesi.zip) |
| Veri kaynağı ve kullanım koşulları | [Veri lisansı](DATA_LICENSE.md) |
| Dosya bütünlüğü | [SHA-256 listesi](SHA256SUMS.txt) |

Tam proje ZIP’i, klasör yapısı korunmuş **89 dosya** içerir. Kaynak kod `src/backprop_wine/`, açıklamalı notebook `notebooks/backprop_wine.ipynb`, yöntem açıklaması `docs/METHODS.md`, deney ayarları `configs/`, veri `data/`, sayısal sonuçlar `results/` ve şekiller `paper/figures/` altındadır. Kurulum ve çalıştırma komutları arşiv çıkarıldıktan sonra proje klasöründe yürütülmelidir.

## Kurulum ve çalıştırma

ZIP’i indirin ve `proje` adlı boş klasöre çıkarın. macOS/Linux örneği:

```bash
unzip Geri_Yayilim_Projesi.zip -d proje
cd proje
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m pip install --no-deps -e .
python scripts/demo_backprop.py
python -m pytest -q
python scripts/verify_results.py
python scripts/run_notebook.py
```

Windows’ta ZIP’i Dosya Gezgini ile çıkarın ve PowerShell’de `.venv\Scripts\Activate.ps1` ile ortamı etkinleştirin. Python 3.12 kullanın. Doğrulanan ortam Python 3.12.15/macOS arm64’tür; diğer işletim sistemleri ayrıca sınanmadı.

Ayrı kurulumda **120 test** ve notebook’un **7 kod hücresi** hatasız çalıştırıldı. Küçük ağın ileri/geri hesabı doğrulandı. Bütünlük betiği **88 dosya özetini** ve kayıtlı metriklerden **42 aritmetik kontrolünü** doğrular. Notebook yeni Wine modeli eğitmez; kayıtlı test sonuçlarını CSV’den okur. Gerçek veri modellerinin baştan eğitimi bu teslim kontrolünde yapılmadı. Yeni deney için komutlar ve kapsam arşiv içindeki README’de açıklanır.

## Veri ve deney

- [UCI Wine Quality](https://archive.ics.uci.edu/dataset/186/wine+quality) · [Resmî ZIP indirme](https://archive.ics.uci.edu/static/public/186/wine%2Bquality.zip) · [DOI](https://doi.org/10.24432/C56S3T).
- Kırmızı veri: 1599 satır ve 11 girdi. Eğitim/doğrulama/test: **1141/229/229** satır. Aynı girdi grubunun farklı bölmelere dağılması engellendi; ölçekleyici yalnız eğitimden öğrenildi.
- Bölme seed’i **42**, eğitim seed’leri **42, 43, 44**. Ana ağ **11–16–1**, tanh gizli katman, doğrusal çıkış, MSE ve SGD kullanır.

| Yöntem | Kayıtlı test RMSE |
|---|---:|
| Eğitim ortalaması | 0.7962 |
| Ridge | 0.6289 |
| Rastgele orman | 0.6250 ± 0.0038 |
| NumPy MLP | 0.6199 ± 0.0070 |
| SVR | **0.5975** |

Daha düşük RMSE daha iyidir. ±, tek sabit bölmede üç eğitim seed’inin örneklem standart sapmasıdır; güven aralığı değildir. Bu test bölmesinde SVR en düşük hatayı vermiştir. Tek bölmeden genel yöntem üstünlüğü çıkarılmaz. Bilimsel sonuçlar ve özgün deney etiketleri korunmuştur.
