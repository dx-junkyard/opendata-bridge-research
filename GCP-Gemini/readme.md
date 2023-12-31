# Gemini Pro の設定とデプロイ

## 概要
GeminiはGoogleが2023年12月に発表した大規模言語モデル(LLM)です。以下の3種類のサイズがあります：
- **Gemini Ultra** — 非常に複雑なタスクに対応する、最大かつ最も有能なモデル。
- **Gemini Pro** — 幅広いタスクに対応するための最良のモデル。
- **Gemini Nano** — オンデバイス タスク向けの最も効率的なモデル。

現在使用可能なのは、**Gemini Pro**と**Gemini Nano**です。ただし、Gemini Nanoはスマートフォン上で動作するLLMです。

詳細は[Introducing Gemini: our largest and most capable AI model](https://blog.google/technology/ai/google-gemini-ai/#performance)をご覧ください。

## 設定
Gemini Proの推論をGoogle Colab及びGoogle AI Studioで実行しました。両方共に設定は簡単です。インターネット上の情報などを見ると、Gemini ProはGPT-3.5と同様の能力を持つとされています。

## 参考資料
- [Build with Gemini](https://ai.google.dev/)
- [It’s time for developers and enterprises to build with Gemini Pro](https://blog.google/technology/ai/gemini-api-developers-cloud/)

---

### Google Colab
1. [Google Colab で Gemini Pro をもっと試す](https://note.com/npaka/n/n1c368639cada)  
   ⇒ これを参考に[notebook](notebook/Gemini%20Pro.ipynb)を作成。2024年始めまでは1分/60回まではAPIは無料のようです。詳細は[利用料金](https://blog.google/technology/ai/gemini-api-developers-cloud/)を参照。
2. [Python Quickstart](https://colab.research.google.com/github/google/generative-ai-docs/blob/main/site/en/tutorials/python_quickstart.ipynb#scrollTo=lEXQ3OwKIa-O)

---

### Google AI Studio (Gemini Pro)
以下が実行イメージです。Google AI Studioは、環境構築に手間がかからないイメージです。
画面右側にTemperatureなどの設定項目があります。  

![Google AI Studio 実行イメージ](data/gemini_pro/JGLUE.png)

---

### Google AI Studio (Gemini Pro Vision)
Google AI Studioでのファイル読み込みの機能が見当たらなかったので、試しにGemini Pro VisionでAED一覧のPDFの画像データを読み込ませてみました。ところどころ間違えがあります。

![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/266e9af9-bf2d-47f6-9a38-fc263737b950)

読み込んだテーブルデータ

![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/659f77bf-523f-4506-9812-a75a59d2a34a)
