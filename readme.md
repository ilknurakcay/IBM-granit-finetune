# Granite Fine-Tuning

Bu proje, **ibm-granite/granite-vision-3.2-2b** modelini **google/wit** veri setinin bir kısmıyla fine-tune etmek için hazırlanmıştır. GPU olmadığı için eğitim süreci sınırlı tutulmuştur.

## Kullanılan Teknolojiler

- Hugging Face **Transformers**
- **TRL (Transformer Reinforcement Learning)**
- **Datasets**
- **BitsAndBytes** (Kuantizasyon için)
- **PEFT** (Parameter Efficient Fine-Tuning)
- **Accelerate**
- **Pandas, NLTK, Requests, PIL**

## Kurulum

Aşağıdaki komutları çalıştırarak gerekli kütüphaneleri yükleyebilirsiniz:

```bash
pip install -q git+https://github.com/huggingface/transformers.git
pip install -U -q trl datasets bitsandbytes peft accelerate cairosvg
```

## Kullanım

Betik, Granite modelini `google/wit` veri setiyle fine-tune etmek için tasarlanmıştır. Çalıştırmak için:

```bash
python granit_fine_tune.py
```

Kodda kullanılan bazı parametreler:
- **USE_QLORA = True** → Bellek kullanımını optimize etmek için kuantizasyon
- **USE_LORA = True** → Hafif ince ayar (fine-tuning) için ağırlık matrisi güncellemeleri

## Veri Kümesi

Fine-tuning işlemi **google/wit** veri setinin bir alt kümesiyle yapılmıştır. `google/wit`, görüntü-kelime eşleşmelerine dayalı bir veri kümesidir ve genellikle görüntü açıklamaları (captioning) ve multimodal model eğitimleri için kullanılır. GPU kullanılmadığı için yalnızca küçük bir kısmı ile eğitim yapılmıştır.

## Model Detayları

- **Model:** IBM Granite Vision 3.2-2B
- **Eğitim Yöntemi:** Supervised Fine-Tuning (SFT) + LoRA
- **Kuantizasyon:** 4-bit QLoRA
- **Optimizasyon:** AdamW optimizer, weight decay 0.01, learning rate 1e-4
- **Eğitim Ortamı:** Google Colab (GPU olmadan, bellek optimizasyonu ile)

## Karşılaşılan Zorluklar

- **Sınırlı Donanım:** GPU olmadığı için QLoRA ve LoRA gibi hafif ince ayar yöntemleri kullanıldı.
- **Küçük Veri Kümesi:** Tüm veri kümesini kullanmak mümkün olmadı.
- **Bellek Yönetimi:** CUDA bellek sınırları nedeniyle eğitim süreci optimize edildi.

## Katkıda Bulunma

Bu projeye katkıda bulunmak için **pull request** gönderebilir veya `Issues` sekmesinde geri bildirim bırakabilirsiniz.

