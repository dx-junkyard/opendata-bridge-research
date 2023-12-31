# Gemini Pro の設定とデプロイ

Gemini Proの推論をGoogle Colab及びGoogle AI Studioで実行しました。以下情報を参考に簡単に設定できました。  
個人的な所感かつかなりおおざっぱですが、GPT-3.5と同様の能力かと思われます。

### Google Colab
1. [Google Colab で Gemini Pro をもっと試す](https://note.com/npaka/n/n1c368639cada)  
   ⇒ これを参考に[notebook](notebook/Gemini%20Pro.ipynb)を作成。2024年始めまでは1分/60回まではAPIは無料のようです。詳細は[利用料金](https://blog.google/technology/ai/gemini-api-developers-cloud/)を参照。
3. [Python Quickstart](https://colab.research.google.com/github/google/generative-ai-docs/blob/main/site/en/tutorials/python_quickstart.ipynb#scrollTo=lEXQ3OwKIa-O)


### Google AI Studio(Gemini Pro)
https://ai.google.dev/    
以下が実行イメージ。Google AI Studioは、環境構築に手間がかからないイメージです。
画面右側にTemperatureなど設定項目があります。  

   ![Google AI Studio 実行イメージ](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/55ce7c23-d020-47a1-9c03-c0fe5a482c9a)

### Google AI Studio(Gemini Pro Vision)
Google AI Studioでのファイル読み込みの機能が見当たらなかったので、試しにGemini Pro VisionでAED一覧のPDFの画像データを読み込ませてみた。
ところどころ間違えがある。

　　![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/266e9af9-bf2d-47f6-9a38-fc263737b950)

読み込んだテーブルデータ

  　![image](https://github.com/dx-junkyard/opendata-bridge-research/assets/115245862/659f77bf-523f-4506-9812-a75a59d2a34a)

