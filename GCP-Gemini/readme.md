# Gemini Pro

## 概要
GeminiはGoogleが2023年12月に発表した大規模言語モデル(LLM)です。以下の3種類のサイズがあります。  
詳細は[Introducing Gemini: our largest and most capable AI model](https://blog.google/technology/ai/google-gemini-ai/#introducing-gemini)をご覧ください。
- **Gemini Ultra** — 非常に複雑なタスクに対応する、最大かつ最も有能なモデル。
- **Gemini Pro** — 幅広いタスクに対応するための最良のモデル。
- **Gemini Nano** — オンデバイス タスク向けの最も効率的なモデル。

> [!NOTE]
> 現在使用可能なのは、**Gemini Pro**と**Gemini Nano**です。ただし、Gemini Nanoはスマートフォン上で動作するLLMです。

> [!tip]
> その他、Gemini Proに関する参考資料
> - [Build with Gemini](https://ai.google.dev/)
> - [It’s time for developers and enterprises to build with Gemini Pro](https://blog.google/technology/ai/gemini-api-developers-cloud/)

## 料金
APIの呼び出しについては、1分間60回までは無料(2024/01/01現在)だが、無料公開が終了すると、以下の通り料金が発生する。  
詳細は[利用料金](https://blog.google/technology/ai/gemini-api-developers-cloud/)を参照。  

| INPUT               | OUTPUT             |
|---------------------|--------------------|
| $0.00025 / 1K characters | $0.0005 / 1K characters |
| $0.0025 / image     |                    |



## 設定
Gemini Proの推論をGoogle Colab及びGoogle AI Studioで実行しました。両方共に設定は簡単です。

### Google Colab
1. [Google Colab で Gemini Pro をもっと試す](https://note.com/npaka/n/n1c368639cada)  
   ⇒ これを参考に[notebook](notebook/Gemini%20Pro.ipynb)を作成。
3. [Googleが公開しているPython Quickstart](https://colab.research.google.com/github/google/generative-ai-docs/blob/main/site/en/tutorials/python_quickstart.ipynb#scrollTo=lEXQ3OwKIa-O)


### Google AI Studio (Gemini Pro ＆ Gemini Pro Vision)
以下が実行イメージです。Google AI Studioは、環境構築に手間がかからないイメージです。
画面右側にTemperatureなどの設定項目があります。  

![Google AI Studio 実行イメージ](data/gemini_pro/JGLUE.png)





### Google AI Studio (Gemini Pro Vision)
Google AI Studioでのファイル読み込みの機能が見当たらなかったので、試しにGemini Pro VisionでAED一覧のPDFの画像データを読み込ませてみました。ところどころ間違えがあります。

![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/266e9af9-bf2d-47f6-9a38-fc263737b950)

読み込んだテーブルデータ

![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/659f77bf-523f-4506-9812-a75a59d2a34a)
