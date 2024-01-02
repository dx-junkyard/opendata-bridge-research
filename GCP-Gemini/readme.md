# Gemini Pro

## 概要
GeminiはGoogleが2023年12月に発表した大規模言語モデル(LLM)です。以下の3種類のサイズがあります。  
詳細は[Introducing Gemini: our largest and most capable AI model](https://blog.google/technology/ai/google-gemini-ai/#introducing-gemini)を確認ください。
- **Gemini Ultra** — 非常に複雑なタスクに対応する、最大かつ最も有能なモデル。
- **Gemini Pro** — 幅広いタスクに対応するための最良のモデル。
- **Gemini Nano** — オンデバイス タスク向けの最も効率的なモデル。

> [!NOTE]
> 現在使用可能なのは、**Gemini Pro**と**Gemini Nano**です。ただし、**Gemini Nano**はスマートフォン上で動作するLLMです。

## 料金

 Gemini APIの利用は、現在1分間に最大60回の呼び出しが可能で、以下の料金が適用されます。  
 最新の料金情報については、[利用料金](https://blog.google/technology/ai/gemini-api-developers-cloud/)を確認ください。

| タイプ                  | INPUT                 | OUTPUT                   |
|-------------------------|---------------------------|---------------------------|
| **テキスト入力**        | $0.00025 / 1K characters        | $0.0005 / 1K characters         |
| **画像入力**            | $0.0025 / image            |                       |

> [!CAUTION]
> 現在、Gemini APIは、無料で利用できます（2024/01/01現在）。無料期間終了後に上記料金が適用されます。


## 利用
Gemini Proは、Google Colab及びGoogle AI Studioで利用可能です。

### Google Colab での Gemini Pro 利用ガイド

以下の方法を参考にしてください。

1. [Google Colab で Gemini Pro をもっと試す](https://note.com/npaka/n/n1c368639cada)：このガイドを参照して、[notebook](notebook/Gemini%20Pro.ipynb)を作成。
2. [Python Quickstart](https://colab.research.google.com/github/google/generative-ai-docs/blob/main/site/en/tutorials/python_quickstart.ipynb#scrollTo=lEXQ3OwKIa-O)：Googleが提供するチュートリアルを実行して、Gemini Proが利用可能です。

> [!TIP]
> API keyは[Google AI Studio](https://makersuite.google.com/app/apikey)から取得できます。



### Google AI Studio での Gemini Pro 利用ガイド
[Google AI Studio](https://makersuite.google.com/)からGemini Proが利用できます。  
以下が実行イメージです。Google AI Studioは、notebookよりさらに環境構築に手間がかからないイメージです。  

#### Gemini Proによるテキスト読み込み
[jcommonsenseqa](https://github.com/yahoojapan/JGLUE/blob/c35b43c73056f6898837de0dcc5ba11cc7dc3ecc/datasets/jcommonsenseqa-v1.1/valid-v1.1.json#L125C6-L125C6)と[elyza/ELYZA-tasks-100](https://huggingface.co/datasets/elyza/ELYZA-tasks-100)を読み込み。質問に対して的確に答えています。  

![Google AI Studio 実行イメージ](data/gemini_pro/JGLUE.png)

#### Gemini Pro Visonによる画像読み込み(1)
フリー素材の写真を読み込み。木があることはもちろん雪が降っていることも的確に説明しています。  

![Google AI Studio 実行イメージ](data/gemini_pro_vision/tree.png)

#### Gemini Pro Visonによる画像読み込み(2)
Gemini Pro Visionで[AED設置施設一覧(門司区)](https://www.city.kitakyushu.lg.jp/files/001024483.pdf)のAED一覧のPDFの画像データを読み込ませてみました。  
テーブルがずれていたり、数値や文字の読み込み間違えがあります。

![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/266e9af9-bf2d-47f6-9a38-fc263737b950)

読み込んだテーブルデータ

![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/659f77bf-523f-4506-9812-a75a59d2a34a)


> [!TIP]
> 画面右側のmodelによりGemini ProとGemini Pro Vison の切り替えができます

## データ抽出
[北九州市公共施設白書（令和４年度状況）](https://www.city.kitakyushu.lg.jp/files/001058942.pdf)のデータを正しく抽出できるのかを確認。  
データをテキストデータとして**Gemini Pro**、画像データとして**Gemini Pro Vision**へプロンプトとして与えた。
> [!NOTE]
> **Gemini Pro Vision**はデータのスクリーンショットをプロンプトとして与えています。  
> データ全てのスクリーンショットを1度で撮れないため、読み込む行列を絞っている形になっています。

### 市営住宅
#### Google AI Studio (Gemini Pro)

#### Google AI Studio (Gemini Pro Vision)

### 市民センター
#### Google AI Studio (Gemini Pro)

#### Google AI Studio (Gemini Pro Vision)


### 環境施設
#### Google AI Studio (Gemini Pro)

#### Google AI Studio (Gemini Pro Vision)

## その他参考資料
- [Build with Gemini](https://ai.google.dev/)
- [It’s time for developers and enterprises to build with Gemini Pro](https://blog.google/technology/ai/gemini-api-developers-cloud/)
